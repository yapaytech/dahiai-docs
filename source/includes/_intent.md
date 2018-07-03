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

## Variable Types

|           Type          | Description | Example |
|:-----------------------:|-------------|---------|
| Text                    | For string values | `Hello`       |
| Int                     | For integer values            |     12456    |
| Regex                   | For string values with regex matching. Needs regex key. | `es123` with regex:`\w{2}\d{3}`|
| Identifier              | For 11 digit country identification number. Only for turkey right now. |  12345678901       |
| Location                | For location value such as location sharing messages |  41.015137,28.979530  |
| Email                   | For email values | myemail@yapaytech.com |
| Phone                   | For phone type values | 05xx322xxxx, +905xx322xxxx, 5xx322xxxx |
| Datetime                | For Date and Time values | tomorrow at 3pm|
| Time                    | For Time values| at 3pm |
| Date                    | For Date Values| 3 day later, tomorrow |
| Array                   | For Text array selections | |
| Horizontal Scroll Array | For Horizontal Card selections |         |
| Multi Array             | For Text array selections with ability to select multiple answer |         |

## Variable Keys options
> ![regex-filter](/images/regex_filter.png)
> ![regex-filter-key](/images/regex_filter_key.png)

1. default: default value for variable if a value is not defined for it.
2. regex_filter: regex detect for type `Text` variable.
3. regex_filter_index: regex group index to select. Needs regex_filter. In the example if a user types test 123 our paramater would put 123 to variable.
4. regex: regex detect for type `Regex` variable.

Regex type is a little bit different from Text type. Text type with regex_filter would try to detect value from first message that triggers this intent and fill the variable but if he can't find a value matches with regex it would ask the variable question to user to fill the variable. In this case user can provide any string answer to this variable without limits of regex. In short in Text type with regex_filter, regex is used only for first time value detection. 

If you want to do a custom matching rules that must be followed by user answer like a project number that has to start with 2 string and end with 3 number you can use `Regex` variable type with regex key defined as `\w{2}\d{3}`. In this case this regex will be used for initial value detection and after when is question asked to user. With this you can set custom rules for variables.

You can alse use `{key}` system to fill variable default value or question. Like you have 2 paramater first one ask's the users name and the second one ask's user email you can define second question like `Hello, {name}. Please provide a valid email for further contact`.



## Variable tojson
> ![tojson](/images/tojson.png)

You can print value of variable to string with tojson helper. You just need to add .tojson() to end of variable name like `{places.tojson()}`. You can also output to operations.



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
> ![create_op](/images/create_op.png)

Operation is a way to trigger an external resource event or save to cache. There are two types of operation. These are as follow...

|         Type | Description                        |
|-------------:|------------------------------------|
| Call Service | Get or Post web request operation  |
|        Cache | Save to cache a variable operation |
| ForwardToAgent | Disables bot and forward the conversation to agent waiting list. |

## Call Operation
> ![operation get](/images/ope-get.png)
Try Get Screen
![operation get try](/images/ope-get-try.png)
Json Picker Button
![operation json picker](/images/ope-get-picker.png)
Json Picker Screen
![operation json picker screen](/images/ope-get-picker-screen.png)
How to use in output section
![operation output](/images/ope-get-output.png)
Demo test for this intent
![operation chat](/images/ope-get-chat.png)

Call Service is a way to interact with external resources or apis. There are two types of Call Service currently available.

| Type | Description       |
|-----:|-------------------|
|  GET | GET Http request  |
| POST | POST Http request |

In these operation types you can use following options

|    Type | Description                                                                                                                                                | Required |
|--------:|------------------------------------------------------------------------------------------------------------------------------------------------------------|----------|
|     Uri | Http request url. Can use our variables here like `http://jsonplaceholder.typicode.com/posts/{id}` | Yes      |
| Headers | Json object as string to use as header. Example: `{"content-type":"application/json"}`                                                                     | No       |
| Data    | Json object as string to use as post body. Example: `{"username":"test"}`. You can also use our variable printing markup here like `{"username":"{name}"}` | No       |
| Try Get | A way to test your endpoint if it's working with our system                                                                                                | No       |

In Try Get screen you can check if your endpoint is working correctly with our system. And save as example data to used in json-picker section. Json picker is a variable generator with gui. You can click the `+` button at the right of the text output to access to json-picker. After that you'll see a screen with mock data from your last try get.

## Cache Operation
> ![op_cache_set](/images/op_cache_set.png)

You can either set or clear a key in user.prop scope with this operation. To use this you need to define your key in first textbox and value in second textbox. For example; `user.prop.lastKey` and `{{key}}`. To use this value in intents you need to start your key with $ character like `{{$user.prop.lastKey}}`.

## ForwardToAgent Operation
This operation disables bot in this conversation and puts the conversation agent waiting list.


## Forward

Forwards are basicly for branching to the other intents with specific conditions or without any. With this, you can use power of modularity. 

For example, you are asking users to their informations. After you get their infos, you want to trigger different intent lets say 'confirm' intent and only over 18 aged user should reach this intent. After it matched with our condition(s), then we will pass the this intent's paramater values to forwarded intent.

You can do it with 4 easy step and these are as follows...

### Creating Forward Panel

1. Press the 'Create New Forward' button.

### Adding Condition

Here we define our condition

> ![Add Condition](/images/forward1.PNG)

1. Press 'Add Condition' button
2. Enter your variable  (For our example : {age})
3. Select your condition type (For our example : greater than or equal )
4. Type your conditional value (For our example : 18)
5. Confirm it

> ![Select Intent](/images/forward2.PNG)

If you want to edit any condition after confirm, you can just click over the condition line then change any part of it.

### Select Intent

1. Select our desired intent (For our example : Confirm)

### Passing Values

> ![Passing Values](/images/forward3.PNG)

1. Press the 'show params' button
2. Enter your variable names or constant 



### Notes

We created one forward with single condition in our example but you can define multi forwards with multi conditions.

The important part is a forward section will only do forward only if previous forwards fails and its all conditions matches.

