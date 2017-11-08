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
Here it will try to access data.id value from body. So we want to send id paramater in id here. As default `{{key}}` would try to read 'key' data from request.body.data object. If you want to access to static data from your template you can use `{{#data.x}}` shown in second schema.

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


## Helpers
### __if helper

## Usage