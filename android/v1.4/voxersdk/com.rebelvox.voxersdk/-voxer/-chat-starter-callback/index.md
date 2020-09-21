[voxersdk](../../../index.md) / [com.rebelvox.voxersdk](../../index.md) / [Voxer](../index.md) / [ChatStarterCallback](./index.md)

# ChatStarterCallback

`interface ChatStarterCallback`

Interface defining callbacks which are called
when user of the sdk starts a new chat

### Functions

| Name | Summary |
|---|---|
| [onConversationStarted](on-conversation-started.md) | `abstract fun onConversationStarted(chat: `[`Chat`](../../../com.rebelvox.voxersdk.chat/-chat/index.md)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Called after [Chat](../../../com.rebelvox.voxersdk.chat/-chat/index.md) is started successfully with other user |
| [onError](on-error.md) | `abstract fun onError(e: `[`Error`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-error/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Called after sdk failed to start the given [Chat](../../../com.rebelvox.voxersdk.chat/-chat/index.md) |
