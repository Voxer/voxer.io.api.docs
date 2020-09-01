[voxersdk](../../index.md) / [com.rebelvox.voxersdk](../index.md) / [Voxer](index.md) / [observeChatList](./observe-chat-list.md)

# observeChatList

`fun observeChatList(callback: (`[`List`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-list/index.html)`<`[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`>) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)

Observe new incoming chats.
This api is idempotent.
Only one first callback is respected until clearChatListObserver is called.

### Parameters

`callback` - 