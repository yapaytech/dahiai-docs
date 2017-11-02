---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---
# Dahi.ai
## About
## Registration

# Bot
## Creation

## Settings

# Intent
## User Says
## Variables
## Output
## Operation
## Forward

# Entity

## Types 
### Array
### Horizontal
# Live
Live-Chat can be described as a messaging system. [http://dahi.ai/live](http://dahi.ai/live)

Dahi.ai composed of two system first is chat bots. Second is messaging system aka. Live-chat. Live-chat is most easy way to provide a user integration system without any hurdle.

Also with live-chat's agent section you can use live-chat as a mix of chat-bot and customer service. With doing so your chat-bot can answer most of the user's questions and if it can't answer user's question can pass the conversation to agents.

Live-chat's some features;

* Provide a javascript chat script that can be added to any website.
* Connect a facebook page to chat-bot system.
* Feature to set when will chat-bot be active. (always or outside of work hours)
* Add wellcome message to your chat-bot.
* Can work with Chat-bot and Customer Service Agents at the same time.

## Live Settings
In this section you can modify your live-chat, add agents, connect live-chat to a facebook chat and more. [http://dahi.ai/live/settings](http://dahi.ai/live/settings)

### Main Settings
Main live-chat settings.

> ![Live-Settings](/images/live-settings.png)

|             Key | Description                                                                                                          |
|----------------:|----------------------------------------------------------------------------------------------------------------------|
|       Chat Name | Live Chat Name                                                                                                       |
|    Product Type | Your product's subscribtion tier. (Free or Premium)                                                                   |
|             Bot | Section to select which bot is connected to live-chat. You can select any of your chat-bot.                          |
| When Bot Active | Section to select when will your bot will be active. Always or Outside of Work Hours (Hidden if bot isn't selected.) |
|   Working Hours | Section to configure your working hours. (Hidden if Always Selected in When Bot is Active)                           |

### Agent Settings
> ![Live-Agent](/images/live-agent.png)

Where you can add or remove your live-chat agents.

To add a agent there are some requirements.

1. You must be owner of the live-chat.
2. The mail adress you're trying to add as a agent must be registered user of dahi.ai.
3. The mail adress you're trying to add as a agent must not be owner or agent of another live-chat.

Adding an agent is easy;

1. Click "Add New" Button at the right of the screen in agent section.
2. Type the mail adress of user you want to add as agent.
3. Click "Add" Button. And that's it.

### Live-Widget Script
> ![Live-Script](/images/live-widget.png)

This is the script you can use to add a live chat that your visitors can use to chat with your chat-bot or agents.
Click "Copy to Clipboard" and paste the script in your website somewhere.

### Live-Widget Script Settings

> ![Live-Script](/images/live-script-general.png)

General Settings

|          Key | Description                                            |
|-------------:|--------------------------------------------------------|
|    Chat Name | Live-chat name that shown to user in live-chat script. |
|    Image Url | Live chat user image that shown to user.               |
|   Width Size | Live chat script width size. (px)                      |
|  Height Size | Live chat script height size. (px)                     |
|        Enoji | Add abilty to send emojis in live-chat                 |
| User Invites | Add abilty to invite other users to chat.              |
| Widget Type  | Widget type. Currently cirle or widgetbox.             |

> ![Live-Script](/images/live-script-register.png)

Register Settings

|          Key | Description                                                           |
|-------------:|-----------------------------------------------------------------------|
| Name Surname | When chat start should live-chat ask for user's name setting.         |
| Email Adress | When chat start should live-chat ask for user's email setting.        |
| Phone Number | When chat start should live-chat ask for user's phone number setting. |

## Live Agent Panel
## Live Web Script

#Integrations
## Facebook



# Introduction

Welcome to the Kittn API! You can use our API to access Kittn API endpoints, which can get information on various cats, kittens, and breeds in our database.

We have language bindings in Shell, Ruby, and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

This example API documentation page was created with [Slate](https://github.com/lord/slate). Feel free to edit it and use it as a base for your own API's documentation.

# Authentication

> To authorize, use this code:

```json
{
  "test":"12",
  "alone":"trust"
}

```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```
> ![alt text](/images/logo.png)
> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).


Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# Kittens

## Get All Kittens


```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

