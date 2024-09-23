# Chat

This table contains functions that interface with chat channels.

* [Chat.GetChannels](https://hake.me/docs/systems/chat#chat-getchannels)
* [Chat.Say](https://hake.me/docs/systems/chat#chat-say-channel-text)
* [Chat.Print](https://hake.me/docs/systems/chat#chat-print-channel-text)
* [Chat.SendChatWheel](https://hake.me/docs/systems/chat#chat-sendchatwheel-text)

---

## `Chat.GetChannels()`​

### Returns

List of channel names.

---

## `Chat.Say(channel, text)`​

### Arguments

* ​`channel`​ - Name of channel to send message to.
* ​`text`​ - Message to send.

---

## `Chat.Print(channel, text)`​

### Arguments

* ​`channel`​ - Name of channel to print message to.
* ​`text`​ - Clientside message to print. Supports HTML.

---

## `Chat.SendChatWheel(text)`​

### Arguments

* ​`text`​ - Message to send. Supports HTML.

### Remarks

Sends a message to everyone on your team as if it was a chat wheel message.
