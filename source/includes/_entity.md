
# Entity
> ![entity-list](/images/entity-list.png)

Entity is a list of object that our bot can use to recognize data or ask question.

For example; if we want to ask user which is their favaurite color. We can fill an `colors` named entity with all known colors and link it to the question with using intent paramaters.

There are currently two types of entity. Array and Horizontal, array is for any data list and horizontal for facebook generic-template outputs.

## Add Entity
> ![entity-list](/images/entity-add.png)

To add a new entity follow these steps:

1. click to `ADD` button at the right top corner in entity list page.
2. Type entity name at left top corner of section.
3. Select which type of entity you want to create array(default) or horizontal. You can't change this after creating an entity.
4. Type your data.
5. Click `SAVE` button to save it.

## Edit Entity
> ![entity-list](/images/entity-colors.png)

To edit an entity click it's name, then you can type any new text in to `Define Item` section and press enter to add it to the list.

In this screen you can also modify any item's name, sysnoms, keys or delete them if you want.

To save click `SAVE` button at right top corner.

## Types
There are currently two types of entity. Array and Horizontal, array is for any data list and horizontal for facebook generic-template outputs.

### Array
> ![entity-list](/images/entity-colors.png)

This is a text based list entity type. Can be used for `array`, `text` and `multi-array` type paramaters.

To add a new element type Reference Value that you want to add in `Define Item` section and press enter.

|             Key | Description                                               | Required |
|----------------:|-----------------------------------------------------------|----------|
| Reference Value | Display text value                                        | Yes      |
|        Synonyms | Equivalents of value to detech for this element.          | No       |
|         Default | is default repiresantation of entity                      | No       |
|            Keys | key-value pairs for this entity, can be used by chat-bot. | No       |

### Horizontal
> ![entity-card](/images/entity-card.png)

This is a horizontal card entity. Can be used for outputing generic-template messages.

|       Key | Description                                                   | Required | Limits                     |
|----------:|---------------------------------------------------------------|----------|----------------------------|
|     Title | Title value for this card item.                               | Yes      | 0-80 Character             |
| Image_url | Image url for this card item.                                 | No       | Must be a valid image url. |
|  Subtitle | Subtitle for this card item.                                  | No       | 0-80 Character             |
|  Item_url | Url to open if this card is clicked.                          | No       |                            |
|     Extra | key-value pairs to define values that can be used by chat-bot | No       |                            |
|   Buttons | Interactive buttons (open web wage, trigger intents, etc.)    | No       | Maximum 3 button           |

#### Buttons
> ![horizontal-button-list](/images/hor-but-list.png)
> ![horizontal-button-web](/images/hor-but-web.png)
> ![horizontal-button-intent](/images/hor-but-int.png)

There is two types of buttons here. One is to open web url, second one is to trigger an intent. You can click to `Add new Button` button and configure what you want to add. 

There are 3 things to chose when adding button. Button text, button type (web_url,postback) and value of the button. For web_url value must be web url. For postback you can chose a intent from combo-box. And click tick button to add button.

<aside class="notice">
Don't forget to click save before exiting to save.
</aside>

Some extra information:

* You can reorder buttons with holding hook at the left of the buttons and drag them.
* To edit buttons click over them.
* To delete button click red trash button.
* To change type of button click the url and arrow button at the center of button edit view. Arrow button represent payload type. Url button for web_url type.