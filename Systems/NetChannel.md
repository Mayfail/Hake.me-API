# NetChannel

This table contains functions concerning the network state of the game.

* [NetChannel.GetLatency](https://hake.me/docs/systems/netchannel#netchannel-getlatency-flow)
* [NetChannel.GetAvgLatency](https://hake.me/docs/systems/netchannel#netchannel-getavglatency-flow)

---

## `NetChannel.GetLatency(flow)`​

### Arguments

* ​`flow`​ - See [Enum.Flow](https://hake.me/docs/globals/enum#enum-flow).

### Returns

A number containing the latency in seconds.

### Remarks

Accurate, but jitters.

---

## `NetChannel.GetAvgLatency(flow)`​

### Arguments

* ​`flow`​ - See [Enum.Flow](https://hake.me/docs/globals/enum#enum-flow).

### Returns

A number containing the *average* latency in seconds.

---
