# GCClient

Table for interacting with the Game Coordinator

* [GCClient.SendMessage](https://hake.me/docs/systems/gcclient#gcclient-sendmessage-protobuf-msgtype-job_id)
* [GCClient.SendHello](https://hake.me/docs/systems/gcclient#gcclient-sendhello)
* [GCClient.GetVersion](https://hake.me/docs/systems/gcclient#gcclient-getversion)
* [GCClient.GetProtobufs](https://hake.me/docs/systems/gcclient#gcclient-getprotobufs)

---

## `GCClient.SendMessage(protobuf, msgtype, job_id)`​

Sends a message to the Game Coordinator

### Arguments

* ​`protobuf`​ - object returned from Protobuf.Create
* ​`msgtype`​ - *optional*

  * Integer that determines the type of the message being sent
  * If this isn't set, the type is automatically determined from the `protobuf`​ that's passed
  * This can be used to substitute other protobuf types if they don't happen to have a message associated with them
* ​`job_id`​ - *optional*

  * Integer that sets the `job_id_source`​ field in the message header (`CMsgProtoBufHeader`​)
  * ​`job_id_target`​ gets set to this in the corresponding response in `OnGCMessageReceived`​ in `msg.GetArguments():msg_hdr.job_id_target`​

---

## `GCClient.SendHello()`​

Sends the initial `CMsgHello`​ to the game coordinator

---

## `GCClient.GetVersion()`​

---

## `GCClient.GetProtobufs()`​

Retrieves a list of all sendable/receivable protobufs known to the client

### Returns

A list of tables with the following fields

* ​`name`​ - string
* ​`type`​ - integer
