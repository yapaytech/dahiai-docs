
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
Click "Copy to Clipboard" and paste the script inside your website's body.

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
