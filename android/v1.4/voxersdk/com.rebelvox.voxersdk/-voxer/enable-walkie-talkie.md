[voxersdk](../../index.md) / [com.rebelvox.voxersdk](../index.md) / [Voxer](index.md) / [enableWalkieTalkie](./enable-walkie-talkie.md)

# enableWalkieTalkie

`fun enableWalkieTalkie(chatId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)

Enable sending audio directly and play received audio automatically. It does not check if the chatId is valid.
There can only be one chatId enabled for walkie talkie. If there is already a chatId enabled for walkie talkie, setting a different chatId will overwrite the old chatId. The new chatId will be the one enabled for walkie talkie. The old chatId will be disabled.

### Parameters

`chatId` - to enable.