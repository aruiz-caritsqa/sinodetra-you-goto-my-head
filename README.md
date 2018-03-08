# sinodetra-you-goto-my-head

> Minimal Sinatra like router for node.js by fapprik... with the added ability to respond with custom headers

## Installation
`npm install sinodetra-you-goto-my-head`

## Usage

At first, (install and) require sinodetra-you-goto-my-head within your script and specify your preferred port (`8000` in this example).

`var app = require('sinodetra-you-goto-my-head')(8000)`

You can refer to [Sinodetra README](https://github.com/fapprik/sinodetra) for a better idea on usage

## Examples
```javascript
app.get('/', function(request, response) {
	response.plain('Hello world!')
})

app.get('/say/:greeting/to/:person', function(request, response, greeting, person) {
	response.html('<b>' + greeting + '</b>, ' + person + '!')
})

app.get('/([0-9]+)/plus/([0-9]+)', function(request, response, one, two) {
	response.plain((parseInt(one, 10) + parseInt(two, 10)).toString())
})

app.error(function(request, response) {
	response.plain('404')
})

// In order to resolve the CORS error when running the server locally
app.get('/healthcheck', (request, response) => {
  console.log(request)
	response.send(
    {active: true},
    200,
    'application/json',
    {'Access-Control-Allow-Origin': "*", 'Access-Control-Allow-Methods': 'POST, GET, PUT, DELETE'}
  )
})  
```

## Contributors
- [fapprik](http://fapprik.com/)
- [@rasshofer](https://github.com/rasshofer)
- [@paulcockrell](https://github.com/paulcockrell)
