```javascript
routes() {
      return client.getEntries().then(entries => {
        return entries.items.map(entry => {
            const type = entry.sys.contentType.sys.id == 'product' ? 'solution' : entry.sys.contentType.sys.id
            // console.log('map: ' + '/'+type+'/' + entry.sys.id);
            return {
              route: '/'+type+'/' + entry.sys.id,
              payload: entry
            };
        }).filter(entry => {
          // console.log('filter: ' + entry.route)
          return entry.route.match(/^\/news\//) || entry.route.match(/^\/solution\//)
        })
      });
    }
````