---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <u>Usefull Links</u>
  - <a href='http://dahi.ai'>Register to Dahi.ai</a>
#  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
#  - errors

search: true
---
# Dahi.ai
## About
## Registration

# Bot
## Creation

## Settings

# Intent
## How to Create Intent?
### Basic Intent - Hello World

> Hello World!
> ![alt text](/images/intent_2.png)

I will show you how to create an easy intent to your bot.
Let's make a Hello World! intent.
This intent has just one job. Whenever user says hello, it will make to your bot response as 'Hello World'.

1. Select your bot from bots list.
2. Click Intents on the left side.
3. Click ADD button in the opening page.
4. Name your intent.
5. Type your inputs on the Define User Says section and press enter.
6. Enter your output text which will be shown to yours.
7. Finally, Save your intent with save button on the upper-right corner.

### Advanced Intent 

## Input

On here, you are defining what user inputs will trigger your intent. You can enter a long sentence here as well as a single word. It's all about what user's input should activate your intent. 

After entered your sentence, you can see each word are clickable. You can select those words for marking them as required word. This mean whenever user enter an input sentence, system check this sentence with each input row and activate it if and only if sentence contains row's all required words.

If there are some unnecessary or wrong sentences you can remove them with delete button on the right side.

## Variables

### What is Variable?

Variable is a value that can change, depending on conditions or on information passed to the intent. It is useful for store the value and use it on other part in the intent such as operation section or forward section.

### How to create Variable?

Enter your variable's name to input area below Define Variable header. After you enter, there will be a row about its attributes. 

### Variable Types



## Output
## Operation
## Forward
## Settings
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
| Edit Persistent Menu | Section to edit your chat-bot's shortcut menu. [For More Information](#persistent-menu)|
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

##### General Settings

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

#### Register Settings

|          Key | Description                                                           |
|-------------:|-----------------------------------------------------------------------|
| Name Surname | When chat start should live-chat ask for user's name setting.         |
| Email Adress | When chat start should live-chat ask for user's email setting.        |
| Phone Number | When chat start should live-chat ask for user's phone number setting. |

#### Color Settings

Where you can change live-chat color palatte.

#### Language Settings

Where you can change live-chat language options or placeholder texts.

## Facebook Integration
> ![Live-Script](/images/live-face-integration.png)

Here you can connect any of your facebook page to live-chat. Any message that your page recieve will be forward to live-chat and vice versa. In live-chat agent section you can view and response to messages your live chat recieve. Or if your live-chat has any chat-bot connected, it will automaticly reply to your customer's questions. This is the easiest way to connect your chat-bot to any facebook page.

To connect a page to live chat follow this steps.

1. Connect to facebook.
2. Give permissions to Dahi.ai Chatbot.
3. Click the "Connect to Page" button at the right of the page list.

## Live-chat Test Page
> ![Live-Test](/images/live-test-page.png)

In the live-chat settings page at the right bottom corner of your screen you will a "Go To Your Client Test Page" Button. This will open a page where you can test your live chat and simulate an user interaction.

![Live-Test](/images/live-test.png)

With this you can test your script and chat-bot before you add it to your website or facebook page.

## Persistent Menu
>![Live-Persistent-Menu](/images/face-persistent.png)
>![Live-Persistent-Menu](/images/live-persistent.png)

Persistent Menu is a way to add shortcut buttons to live-chat and provide user with some go to options. You can add payload or web_url buttons in persistent menu.

Payload buttons will trigger an intent start event when user will click on them. With this button you can add some shortcuts to your intents.

Web_Url buttons will trigger an open web-view event in mobile and open url in new tab in pc. With this you can forward your users some external sites or resources like when an user want to buy your latest song you can put a link to your itunes page here.

Some extra information

* Persistent Menu is supported both by facebook messenger and live-chat script.
* You can have maximum 3 buttons in facebook.
* You can reorder your buttons using hook at the right of the buttons in persistent menu editor. (visible when mouse is hovered in a line)
* Support for more button and nested buttons are in development. When it's ready we'll be updating this editor section.

![Persistent-Menu](/images/persistent.png)

## Live Agent Panel
> ![Live-Agent](/images/agent-panel.png)

Live Agent Section is where you can see your live-chat conversations, join them to answer user's questions where your bot is not able to or see whether your chat-bot did stuck at some type of questions. 

This is where you and your agents can interact with live-chat and your customers.

Here you can select an user at the right of the screen and see their conversation history.
If you want to join the chat and answer instead of chat-bot you can click the "Join Conversation" Button at the right top corner of the panel. And when you want to give back the conversation to chat-bot just click the "Leave Conversation" Button.

At the right of the screen you can see 3 tabs at the top of the users list. You can use this options to filter users.

* All: Every user that is currently is talking to bot or you.
* Open: Every user that is currently is talking to bot or no-one.
* Bound: Every user that is currently is talking to you.

If a conversation is bound to any agent, bot will not answer any question that customer is asking. So to enable bot again either you should leave conversation when you don't want to talk to the user anymore or end the conversation if you think is user won't be asking any more question anytime soon.

Some extra information

* At the right bottom corner of user images in user list you can see which platform user is coming from.
* At the left of the names of user in user list you can see if the user is online or not. (green for online, grey for offline)
* If you click the big (i) button or name of the user at the top of the message panel you can see more information about this user.
* At the left of the join button you can see if the current conversation is bound to whom or is bount to bot or not.

## Live Analytics
> ![live-analytics](/images/live-analytics.png)

Here you can find some usefull information about your live-chat bot and usage information. Currently this section is in development.

# Introduction
# Extras


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

