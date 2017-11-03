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

> ![alt text](/images/intent_inp_1.png)


|   Key    | Description                                                                                                                                      |
|:--------:|--------------------------------------------------------------------------------------------------------------------------------------------------|
|   Name   | Name of your variable. It must be unique.(Required)                                                                                              |
|   Type   | Variable type. You can choose one of the 12 types in the list such as Text, Array etc. Please look Variable Type for further info. (Required)    |
|  Entity  | Required for only array-like variable types. You can select from your entities or system entities.                                               |
| Question | If variable has no value, system will prompt this area text to user and will set the answer to this variable. (Required)                         |
|  Details | You can set some specific values to your variable in here such as regex or default value. For further info please look Extras section.           |
|  Remove  | This button will remove the variable row.                                                                                                        |

> ![alt text](/images/intent_inp_2.png)

After filling all required areas now your variable is ready to use it. 
In anywhere in the intent you can call your variable with {$myVariableName}. 

### Variable Types

|           Type          | Description | Example |
|:-----------------------:|-------------|---------|
| Text                    | For string values | `Hello`       |
| Int                     | For integer values            |     12456    |
| Identifier              | For 11 digit country identification number. Only for turkey right now. |  12345678901       |
| Location                | For location value such as location sharing messages |  41.015137,28.979530  |
| Email                   | For email values | myemail@yapaytech.com |
| Phone                   | For phone type values | 05xx322xxxx, +905xx322xxxx, 5xx322xxxx |
| Datetime                | For Date and Time values | tomorrow at 3pm|
| Time                    | For Time values| at 3pm |
| Date                    | For Date Values| 3 day later, tomorrow |
| Array                   | For Text array selections | |
| Horizontal Scroll Array | For Horizontal Card selections |         |
| Multi Array             | For Text array selections with abilty to select multiple answer |         |

## Output
> ![intent-output-text](/images/intent-output-text.png)
> ![intent-city](/images/intent-city.png)
> ![intent-city-test](/images/intent-city-test.png)

Output section is to define what will bot reply to user at the end of this intent. If you don't want to send a message at the end of this intent you can leave this section empty. There are couple of types of outputs like text, typing, image, video...

|             Type | Description                                                           |
|-----------------:|-----------------------------------------------------------------------|
|             Text | Plain text message type.                                              |
|           Typing | Sending typing... message and wait x sec before sending next message. |
|            Array | Send a text message with a array of buttons.                          |
| Horizontal Array | Send a generic-template type message with cards.                      |
|            Image | Send a image.                                                         |
|            Video | Send a video                                                          |
|           Custom | Send a custom formatted text. (for custom api and endpoint usage).    |

You can create more than one output for the same intent. To do so just click the `CREATE NEW OUTPUT` button.


To use variables in your intent you can use `{<key>}`. For example if our paramater name is city. We can get city name in output like this `Weather status for {city} is sunny`. If you want to key-extra values you can chain with `.` like a normal json object. For example in our `sys.city` entity we have plate code for each city of Turkey in `code` keyword. We can use it like this `{city.code} is the plate number of {city} city.`.

Or if you want to print something from `GET` or `POST` operation you can use `return` variable name like `{return.name}`.

## Operation
Documentation coming soon...

## Forward
Documentation coming soon...