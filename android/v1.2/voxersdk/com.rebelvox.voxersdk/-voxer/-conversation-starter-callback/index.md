[voxersdk](../../../index.md) / [com.rebelvox.voxersdk](../../index.md) / [Voxer](../index.md) / [ConversationStarterCallback](./index.md)

# ConversationStarterCallback

`interface ConversationStarterCallback`

Interface defining callbacks which are called
when user of the sdk starts a new conversation

### Functions

| Name | Summary |
|---|---|
| [onConversationStarted](on-conversation-started.md) | `abstract fun onConversationStarted(conversation: `[`Conversation`](../../../com.rebelvox.voxersdk.conversation/-conversation/index.md)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Called after [Conversation](../../../com.rebelvox.voxersdk.conversation/-conversation/index.md) is started successfully with other user |
| [onError](on-error.md) | `abstract fun onError(e: `[`Error`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-error/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Called after sdk failed to start the given [Conversation](../../../com.rebelvox.voxersdk.conversation/-conversation/index.md) |
