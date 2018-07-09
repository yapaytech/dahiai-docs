# Api
> To use our endpoint you need to use this code:

```shell
curl -X POST \
  http://api.dahi.ai/dh/bot/tkn/59fff527e4b0cf33abf0c959 \
  -H 'content-type: application/json' \
  -H 'x-requested-with: XMLHttpRequest' \
  -d '{"recipientId":"user_id" , "message":{ "text":"yemek","type":"text"}}'
```
> Make sure to replace `user_id` with a user_id and `59fff527e4b0cf33abf0c959` with your bot id.

```json
# request body example, (message.text is required)
{
  "recipientId": "user_id",
  "message": {
    "text": "message_text",
    "type": "text"
  }
}


# response body example, there are more information that is removed from this example.
{
  "result": {
    "messages": [{
      "type": "array", // Message Type
      "values": [ // Buttons for array type message
        {
          "text": "Dışarıda Yemek İstiyorum",
          "extra": {
            "kisa": "Dışarıda",
            "payload": "59fff930e4b0cf33abf0c984_16"
          }
        },
        {
          "text": "Burada Yemek İstiyorum",
          "extra": {
            "payload": "59fff930e4b0cf33abf0c984_17"
          }
        }
      ],
      "text": "Nerede Yemek İstersiniz?" // Message Text
    }],
    "conversation_id": "conversation id"
  }
}
```
You can use our dahi.ai chat-bot platform with our endpoint.

You can learn your bot's bot_id (bot token) from bot settings page.

`http://api.dahi.ai/dh/bot/tkn/{bot_id}`

From response `result.messages` array is the response messages array.