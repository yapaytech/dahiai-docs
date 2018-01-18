# Template
## What is Template
> ![template-list](/images/template-list.PNG)
> ![template-edit](/images/template-edit.PNG)

Template is a way to create message data that supported by dahi.ai. If you want to create a horizontal scroll array message from your REST api data, you can use template feature to create a middleware REST api.

When you created a template if you revisit it's edit page you will see a url like `https://template.maytap.me/service/59f71e0de0aadb6b3ec6256c` that you can use to access to this template from any service. You'll get a unique id for each one of your templates. This REST service can be called with `GET` and `POST` methods. You can find more information in `USAGE` section

Template system is new and still under development and curently is `BETA` stage. When we update this system your old schemes might break.

Also our variable access system in template is different from dahi.ai's chat-bot system.

## Main Paramaters
Here are some descriptions of which paramater means what.

|     Key | Description                                                                                               | Default    | Type   | Required |
|--------:|-----------------------------------------------------------------------------------------------------------|------------|--------|----------|
|    name | Label for template, used to identify your templates from each other                                       | No Default | String | No       |
|     uri | If your template needs to call a external `REST` service to extract data from you need to define it here. | No Default | String | No       |
|  method | Which method used to call your uri call. `GET` or `POST`                                                  | GET        | String | No       |
|    dahi | Which shema                                                                                               | 0          | Number | No       |
| data    | Static data that can be used by this template with `{{#data.variableName}}`                               | {}         | Object | No       |
| schemas | Schemas array. Look at shemas section for more information                                                | []         | Array  | Yes      |

For uri you can use your static data or post data values. For more information check Paramater System Section

## Schemas
> ![template-schema](/images/template-schema.PNG)

```json
// Output examples from this schema
// GET https://template.maytap.me/service/59f71e0de0aadb6b3ec6256c
{
  "multi_message": true,
  "messages": [{
      "type": "text",
      "text": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit is where"
    },
    {
      "type": "text",
      "text": "qui est esse is where"
    },
    {
      "type": "text",
      "text": "ea molestias quasi exercitationem repellat qui ipsa sit aut is where"
    },
    {
      "type": "text",
      "text": "eum et est occaecati is where"
    }
  ]
}

// GET https://template.maytap.me/service/59f71e0de0aadb6b3ec6256c?s=1&data.y=12
{
  "multi_message": true,
  "messages": [{
    "type": "text",
    "text": "12 15"
  }]
}
```

Shema is a mapping style to used to create a output data. Your uri, method, data, REST Response from your uri, post body, query paramaters etc. can be used here. There are some keywords helper can be used here other than that you can also use Paramater System to import data to string values. Chat-bot system uses a specific message recognition from Call Service Operation if response from a Call Service is json and has `{multi_message:true,messages:[]}` Keyword it'll automaticly try to look messages array to and create messages from this array to send to the user. And objects in this array must be message formatted objects. For text message it can be like this `{type:"text",text:"Hello, World!"}`. This will create a `Hello, World!` message and send it as a response to the user. Because it's an array you can send multiple messages in one request call.

In this example there are two schemas first one has `__each,__type,__limit` helpers and `type,text` key-value pairs. You can find more information in Helpers Section and how `{{}}` works can be found in Paramater System.

We're adding more helpers and features according to the customers needs. If you think a helper would improve or help customers to create their templates easly you can contact us through `info@yapaytech.com`. Your suggestion must not break old shemas.

## Paramater System
Paramater system currently can be used in 3 section `__if` helper, `uri` string for template and `string` values in schema. Check helpers section for more information for __if helper.

### URI
```shell
curl -X GET \
  'https://template.maytap.me/service/59f71e0de0aadb6b3ec6256c?data.id=2'

or

curl -X POST \
  https://template.maytap.me/service/59f71e0de0aadb6b3ec6256c \
  -H 'content-type: application/json' \
  -d '{"data":{"id":1}}'
```

First of all let's say we want to pass a paramater to uri from post body we use to call template endpoint or get query paramaters to call template endpoint. At this point of system (creation of url) you have access to static data from template object, and body object. More info about body object can be found in Usage Section.

For example let's say our uri is like this `https://jsonplaceholder.typicode.com/posts/{{id}}`.
Here it will try to access data.id value from body. So we want to send id paramater in data here(As shown in examples at right section). As default `{{key}}` would try to read 'key' data from request.body.data object. If you want to access to static data from your template you can use `{{#data.x}}` shown in second schema.

### In string values

```json
// Example url: https://template.maytap.me/service/59f71e0de0aadb6b3ec6256c?s=1&data.y=12
// Schema object used in this example
{
  "name": "test",
  "uri": "https://jsonplaceholder.typicode.com/posts",
  "method": "GET",
  "dahi": 0,
  "data": {
    "x": "15"
  },
  "schemas": [{
      "__each": "",
      "__type": "custom",
      "__limit": 4,
      "type": "text",
      "text": "{{title}} is where"
    },
    {
      "text": "{{#body.data.y}} {{#data.x}}",
      "type": "text",
      "__type": "custom"
    }
  ]
}

// Output from example
{
  "multi_message": true,
  "messages": [{
    "type": "text",
    "text": "12 15"
  }]
}
```

Here `{{key}}` would try to read from cursor. Cursor is most of the time would point at response recieved from uri request. But if it's inside an `__each` helper object it would point at array's object that currently used to create this iteration. More info `__each` helper section.

other then that you can access to scope with using # tag. If you want to access to request body that you used to call template you can use `{{#body.x}}` like if i use `https://template.maytap.me/service/59f71e0de0aadb6b3ec6256c?s=1&data.y=12` url to call my template (Look at Schema object used in this example) in this call our body object would be `{s:1,data:{y:12}}` here s:1 means use schemas[1] to create our output. our output text is `{{#body.data.y}} {{#data.x}}` (from schema[1]) and created output shown at right section. Here you can see #body.data.y and #data.x used. As you can guess you can access to body with #body tag and #data is used to access to template.data object. In this schema it's just creating a simple message combining a static data stored inside template.data object and a variable from get url call.

Let's say your api response is `{"arr":[1,2,3,4]}` and you want to print second element from arr array. To do so you can use `{{arr[1]}}` to print it.

Another example with `{"test":{"text":"hello"}}` response data to print hello world we can use `{{test.text}}, World!` complete shema would look like this. `{{__type:"custom",type:"text",text:"{{test.text}}, World!"}}`. Here __type would wrap our object inside `{multi_message:true,messages:[<here our object would be put>]}` so dahi.ai can understand that this template a message printing operation. type:"text" is defines what type of message is this. and text would be what will be sended to the user.

### Javascript and Accessible libraries
If you stuck with the thing you want to do and can't do with other tools you can always use javascript. To use javascript you need to start with an `$` character like `{{$[1,2,3].join(',')}}`. You can access to current cursor with `item` variable like `{{$item.title.replace('test','')}}` and can access to scope with `__root` keyword.
Like if you want to access to data You could use `{{#body.data.y}}` would be equal to `{{$__root.body.data.y}}`.

Libraries that can be accessed from inside of javascript code are as follow; `Moment.js (moment)`[docs](https://momentjs.com/docs/), `lodash (_)`[docs](https://lodash.com/docs/)

### Html tags clear helper
This is a simple clear helper to clear tags like `<br>` or `\n\t`. It's simple as it gets you just need to add `!` to start of `{{}}` like `{{!title}}`. It would get title and then clear extras.


## Helpers
Helpers are there to make things easier or add some features that you can do with basic features.

Priority of helpers, and their sub keywords.

|     Order | Sub Keys                  |
|----------:|---------------------------|
|    __type | none                      |
|    __html | none                      |
| __request | none                      |
|    __each | __next, __limit, __filter |
|      __if | __then, __else            |
| __num     | __next                    |
| __json    | __next                    |
| __run     | none                      |

### __if helper
```json
// shema examples
// get every finished work
{
  "__each":"",
  "__type": "custom",
  "__if": "{{completed}}",
  "__then": {
    "type": "text",
    "text": "Finished Work - {{title}}!"
  }
}

// get every work and tag
{
  "__each":"",
  "__type": "custom",
  "__filter": "{{completed}}",
  "__next": {
    "type": "text",
    "text": "Finished Work - {{title}}!"
  }
}
```

__if helper uses two more paramaters. They are __then and __else. __if helper takes a string value that filled with javascript condition code like `true`, `'{{finished}}==='yes'`, `{{id}} > 1`, `'{{name}}'.length > 20` , etc. As you can see you can use our Paramater System inside this string. If this value is true it'll use __then's value as generator, if not true it'll use __else's value as generator. If it looks for __then's or __else's value and can't find one it'll generate null. __then and __else value can be anything that is valid as 

For example; Let's create a template that uses `https://jsonplaceholder.typicode.com/todos` api. We want to print messages according to the todo's `completed` status. If it's completed we want to add `Finished` tag to start of items text data. In example we created there are two schemas. First one returns only the ones that has `completed:true`. Second one prints every one but adds `Finished Work` or `Not Finished Work` to start of the text according to the `completed` value.

## __each helper
This is a foreach operation. It's value should point to a json array. If array is root of the json response `__each`'s value should be `""`.

For example let assume our request from external service is `{test:[{key:1},{key:2}]}` and our schema is `{__each:"test",number:"{{key}}"}` would generate `[{number:"1"},{number:"2"}]`.

### __limit helper for __each
This is a helper for __each helper to put a limit to how much item would you like to return maximum. Value must be a integer.

### __filter helper for __each
This is a helper for __each helper to filter arrays. It works same as __if helper but would be applied to each element before processing __each helper.

### __next helper for __each
This is a helper to wrap what should be used for __each iteration elements.

## __type helper
```json
// Example horizontal type Schema
{
  "__type": "horizontal",
  "__limit": 2,
  "title": "{{title}}",
  "subtitle": "subtitle {{title}}",
  "image_url": "",
  "buttons": [],
  "__each": ""
}

// Example horizontal type Output From Schema
{
  "multi_message": true,
  "messages": [{
    "type": "horizontalscrollarray",
    "values": [{
        "image_url": "",
        "buttons": [],
        "subtitle": "subtitle delectus aut autem",
        "title": "delectus aut autem"
      },
      {
        "image_url": "",
        "buttons": [],
        "subtitle": "subtitle quis ut nam facilis et officia qui",
        "title": "quis ut nam facilis et officia qui"
      }
    ]
  }]
}


```
This a wrapper helper. Value generated from this object would be wrapped inside __type's wrapper. There are currently 2 wrappers `custom` and `horizontal`.

`custom` wrapper would wrap output object inside a dahi.ai chat-bot send message operation format. `{multi_message:true,messages:[<here our object would be put>]}`. If the object that will be wrapped is array it would append to messages array. The object inside messages array must be a dahi.ai message formatted object like `{type:"text",text:"Hello, World!"}`.

`horizontal` wrapper would wrap output object inside a dahi.ai chat-bot horizontal message type. Look at example for more information.

## __request helper
```json
// Get Example
{
  "__request":{
    "uri":"https://jsonplaceholder.typicode.com/todos",
    "then":{
      "__each":"",
      "__limit":3,
      "text":"{{title}}"
    }
  }
}

// Output of example above
[
  {
    "text": "delectus aut autem"
  },
  {
    "text": "quis ut nam facilis et officia qui"
  },
  {
    "text": "fugiat veniam minus"
  }
]

// Post Example
{
  "__request":{
    "uri":"https://jsonplaceholder.typicode.com/todos",
    "method":"post",
    "body":{
      "id":3,
      "title":"product title {{name}}"
    },
    "then":{
      //if you want to do something with response
    }
  }
}

```
This is a tool to call external services. You can find an example of it at right section.

Some more info about it;

|     Key | Description                                                                                               | Default    | Type   | Required |
|--------:|-----------------------------------------------------------------------------------------------------------|------------|--------|----------|
|     uri | If your template needs to call a external `REST` service to extract data from you need to define it here. | No Default | String | Yes      |
|  method | Which method used to call your uri call. `GET` or `POST`                                                  | GET        | String | No       |
|    body | Body data if we want to post something.                                                                   | {}         | Object | No       |
|    then | Uses the response from request to continue with schema.                                                   | No Default | Schema | No       |
| headers | Headers used with request.                                                                                | {}         | Object | No       |

## __run helper
```json
// Example 2 Schema which this schemas are in a template which it's id is "5a09415f91be0e2aef74b452"
[
  {
    "__run":"5a09415f91be0e2aef74b452.1",
    "__next":{
      "text":"From 0. Schema, {{text}}"
    }
  },
  {
    "__run":"5a09415f91be0e2aef74b452.2"
  },
  {
    "text":"From 2. Schema"
  },
  {
    "__run":"5a09415f91be0e2aef74b452"
  }
]

// Call url https://template.maytap.me/service/5a09415f91be0e2aef74b452
{
  "text":"From 0. Schema, From 2. Schema"
}

// Call url https://template.maytap.me/service/5a09415f91be0e2aef74b452?s=3
{
  "text":"From 0. Schema, From 2. Schema"
}

```

This is a helper to run another schema with current objects. This is a jump helper to access your other helpers.

In example we created a template with 4 schema and called first and fourth schema. When we call first schema it calls `"5a09415f91be0e2aef74b452.1"` schema which is [1] indexed schema of `"5a09415f91be0e2aef74b452"` template and continues to __next with the data retrieved from that schema and generates output `"From 0. Schema, From 2. Schema"`.

### __next helper for __run
When __run is used alone it would return the data from the template called but if you want to use that data use create something else you can add __next to same level as __run and continue your schema from there.

## __num helper
```json
// Schema
{
  "parsed_number":{ "__num" : "0.2" }
}

// Output
{
  "parsed_number":0.2
}
```

This is a helper to parse numbers from string. In example we put static `"0.2"` string but you can put the number with `"{{number}}"`.

## __json helper
```json
// Schema for __json
{
  "parsed_json":{ "__json" : "{\"test\":\"test text\"}" }
}

// Output for __json
{
  "parsed_number":{ "test": "test text" }
}
```

This is a helper to parse json from string.

### __next helper for __json
```json
// Schema for __json with __next
{
  "parsed_json":{
     "__json" : "{\"test\":\"test text\"}",
     "__next":{
       "next_next": "last {{test}}"
     }
  }
}

// Output for __json with __next
{
  "parsed_number":{ "next_next": "last test text" }
}
```
This is a helper to continue schema with data parsed from json string. In example we put static `"{\"test\":\"test text\"}"` string but you can define it with `"{{json}}"` with external stringfied text.

## __html helper
```json

// Example Template
{
  "uri":"https://www.lipsum.com/feed/html",
  "schemas":{
    "__html":{
      "title":"{{#Inner > h1}}",
      "paragraphs":{
        "__each":"#lipsum p",
        "text":"{{$$(item).text()}}"
      }
    },
    "sys":"from {{title}}",
    "texts":{
      "__each":"paragraphs",
      "__next":"{{text}}"
    }
  }
}

// Outpu from example above
{
  "texts": [
    "Lorem ipsum dolor sit amet, consectetur adipiscing elit. In in tincidunt purus. Nunc et justo augue. Cras ut fringilla erat. Fusce quis aliquam elit, vitae cursus dui. Nam interdum neque a auctor congue. Fusce facilisis arcu ut odio accumsan, nec vehicula libero auctor. Maecenas lorem neque, interdum ac magna ut, bibendum egestas ipsum.",
    "Sed mauris dolor, pharetra nec urna eu, eleifend fringilla felis. Aenean laoreet aliquet libero eu efficitur. Donec a augue lectus. Etiam in lacinia nulla, vitae pellentesque nunc. Phasellus hendrerit mattis posuere. Nulla condimentum, sapien a scelerisque bibendum, neque tellus laoreet nisi, at bibendum dolor mi eget dui. Sed id lorem finibus, pellentesque nulla eu, scelerisque dolor. Nulla sed lectus dolor. Nulla accumsan felis pharetra nibh porta, non egestas dui placerat. Donec fringilla leo ac sem tempus, sed porttitor diam malesuada. Suspendisse quis arcu risus. Maecenas tempor ultricies tellus, nec pharetra elit vulputate in. Nam leo ante, mollis sit amet mollis et, vehicula ac velit.",
    "Cras tincidunt efficitur lacus non varius. Curabitur scelerisque nulla non mauris vehicula tempus. Aenean tellus sapien, mollis eget odio sed, posuere efficitur diam. In suscipit blandit eleifend. Suspendisse fringilla urna ac quam feugiat, efficitur feugiat enim viverra. Quisque congue purus eget finibus volutpat. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Vivamus varius pharetra convallis. Integer ullamcorper quam libero, eget elementum eros dapibus a.",
    "Ut elit ipsum, faucibus vitae elit quis, finibus viverra velit. Pellentesque magna sem, fringilla quis finibus id, egestas ut nunc. Nullam sit amet neque finibus, lacinia mi id, interdum magna. Donec eget ligula sem. Mauris sodales est in efficitur maximus. Duis quis convallis risus, at gravida nulla. Duis tempor commodo neque, ac mattis odio malesuada vel. Phasellus tempus dui eu congue dictum. Vivamus suscipit efficitur sapien, nec faucibus quam. Etiam porttitor ante in bibendum iaculis. Curabitur diam lectus, dapibus in arcu at, interdum accumsan leo. Quisque vulputate libero in neque lacinia, in elementum neque pulvinar.",
    "Sed vel blandit ligula, a mattis libero. Suspendisse in velit felis. Morbi eleifend turpis ut lacus facilisis, vitae varius enim hendrerit. Proin a dictum odio. Ut ut est vehicula, feugiat massa eget, rhoncus nibh. Phasellus ac magna porta, venenatis sapien vitae, elementum ipsum. Donec in libero non turpis pretium rutrum nec sit amet erat. Praesent dapibus sed quam sed tincidunt. Mauris luctus ultrices risus, ultricies fermentum libero convallis ut."
  ],
  "sys": "from Lorem Ipsum"
}

```

This is a parser with different rules. Basic `"{{key}}"` rule still works. But instead of key's we need to give it some css selector or javascript code to get what we want. In first example we're using __each to get an array of items then uses them to define values for items. `__html` helpers would work before other helpers and replace current cursor with crawled data. The helpers work after `__html` helper would use the cursor from it.

In example there is 2 different usage way to get data first is `{{#Inner > h1}}` and second is `{{$$(item).text()}}`; Actualy first one is almost same as second but it's short way to write and don't need much knowledge about jquery or cheerio. `{{#Inner > h1}}` would be equal to `{{$$('#Inner > h1').text()}}` if it's not inside in an __each helper. If it's inside of a __each helper it would mean `{{$$(item).find('#Inner > h1').text()}}`.

### __each helper for __html
You can use it like this `{"__html":{"__each":"#item-list .product","title":"{{h1}}"}}`. In this example it would get the dom elements with `product` class inside a dom that it's id is `item-list`. Then for each product it would try to find an `h1` tagged dom and put's it's text to title keyword. This would create an array with products titles like `[{"title":"item 1"},{"title":"item 2"},{"title":"item 3"}]` and put it as our cursor. Next we can do something with this like: `{"__html":{"__each":"#item-list .product","title":"{{h1}}"},"__each":"","last":"{{title}}"}` and it would generate `[{"last":"item 1"},{"last":"item 2"},{"last":"item 3"}]`.

Note: Inside __each you don't need to use `{{}}` like normal __each.

### How to use advanced features
You can use any features from popular nodejs library for html dom parsing [cheerio (Go to Cheerio docs)](https://github.com/cheeriojs/cheerio). To use it you need to put a `$` sembol to start of `{{}}` paramater system like `{{$}}` then you can write cheerio code inside of it. You can access to current cursor object with `item` variable like `{{$$(item).find('img').attr('src')}}` this would search for img tagged element and get it's src attribute. For more information you can check cheerio docs.

## Usage
```json
// Template
{
  "uri":"https://jsonplaceholder.typicode.com/posts/{{id}}",
  "method":"GET"
}

// Call url https://template.maytap.me/service/5a09415f91be0e2aef74b4d3?data.id=1&raw=true
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
}

// Call url https://template.maytap.me/service/5a09415f91be0e2aef74b4d3?data.id=2&raw=true
{
  "userId": 1,
  "id": 2,
  "title": "qui est esse",
  "body": "est rerum tempore vitae\nsequi sint nihil reprehenderit dolor beatae ea dolores neque\nfugiat blanditiis voluptate porro vel nihil molestiae ut reiciendis\nqui aperiam non debitis possimus qui neque nisi nulla"
}

// Template
{
  "uri":"https://jsonplaceholder.typicode.com/posts/{{id}}",
  "method":"GET"
}

// Post to url https://template.maytap.me/service/5a09415f91be0e2aef74b4d3
{
  "data":{
    "id":1
  },
  "raw":true
}

// Response
{
  "userId": 1,
  "id": 1,
  "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
  "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
}
```

What template api looks when a request made is id of your template, index of which schema you want to use `s:0 default`. Data to use in uri creation or to post to external server. Should response generated with dahi schema `dahi:false default`. 

If we combine these we'll get a object like this: `{s:0,data:{},id:"5a0407686090c8750ae9baa9",dahi:false}`. For more example look at right section.

### How to get raw response to debug
If you add ?raw=true to your url or add raw:true to your request json if you are using post method. With this you can debug what our system recieves before generation a output data from external api that defined from uri. example url: `https://template.maytap.me/service/5a0407686090c8750ae9baa9?raw=true`.

### With GET Call
In this method `(When template.method="GET")` data would be used to generate uri. Let's say our uri in template is `https://jsonplaceholder.typicode.com/posts/{{id}}`. It needs id to generate this uri so need to pass id value inside data object so our call uri needs to be `https://template.maytap.me/service/<id>?data.id=1`. This uri would generate `{s:0,data:{id:1},dahi:false}` object and send it to template.

### With POST Call
It's same with get method but in this we're sending all the information in request body.

### Template's POST Method
In previous sections we have examples that uses method `GET`. For template that uses `POST` there is just a small difference. data from `{s:0,data:{},dahi:false}` would be used as request body to call your uri that defined in template.
