# dialogs

Non-blocking `confirm`, `alert` and `prompt` dialogs.

Theses native counterparts block the UI thread, are are not allowed in electron and some chrome extention contexts.


# methods

``` js
var Dialogs = require('dialogs')
```

## var dialogs = Dialogs(opts={})

opts.ok default OK

opts.cancel default Cancel

opts.hostname default location.hostname

opts.icon optional url for icon

## dialogs.alert([text], cb)
## dialogs.prompt([text], [default], cb)
## dialogs.confirm([text], cb)
## dialogs.cancel()

Shortcut to cancel the open dialog if exists.

# example

``` js
const Dialogs = require('dialogs')
const dialogs = Dialogs()
dialogs.alert('okidoki', ok => {
  console.log('alert', ok)
  dialogs.confirm('ok?', ok => {
    console.log('confirm', ok)
    dialogs.prompt('username', 'joe.smith@gmail.com', ok => {
      console.log('prompt with default', ok)
      dialogs.prompt('username', ok => {
        console.log('prompt', ok)
      })
    })
  })
})
```

# license

MIT 

Note: Modified style with respect to the original's author code
