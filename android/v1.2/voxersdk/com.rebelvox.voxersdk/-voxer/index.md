[voxersdk](../../index.md) / [com.rebelvox.voxersdk](../index.md) / [Voxer](./index.md)

# Voxer

`class Voxer`

Entry point for the Voxer SDK

### Types

| Name | Summary |
|---|---|
| [ConversationStarterCallback](-conversation-starter-callback/index.md) | `interface ConversationStarterCallback`<br>Interface defining callbacks which are called when user of the sdk starts a new conversation |

### Functions

| Name | Summary |
|---|---|
| [clearChatListObserver](clear-chat-list-observer.md) | `fun clearChatListObserver(): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Stop observing new chats |
| [createUser](create-user.md) | `fun createUser(username: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, appSecret: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, appId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, firstName: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, lastName: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, avatarUri: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, callback: (`[`Boolean`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html)`) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Create new user in Voxer network |
| [disablePrimaryWalkieTalkieMode](disable-primary-walkie-talkie-mode.md) | `fun disablePrimaryWalkieTalkieMode(threadId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Disable primary walkie talkie mode for give threadId |
| [enablePrimaryWalkieTalkieMode](enable-primary-walkie-talkie-mode.md) | `fun enablePrimaryWalkieTalkieMode(threadId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Enable primary walkie mode for given threadId |
| [getChats](get-chats.md) | `fun getChats(callback: (`[`List`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-list/index.html)`<`[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`>) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Get list of chats |
| [getLoggedInUser](get-logged-in-user.md) | `fun getLoggedInUser(): `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)<br>Get already logged in user |
| [login](login.md) | `fun login(username: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, appSecret: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, appId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, callback: (`[`Boolean`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html)`) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Log into Voxer network |
| [logout](logout.md) | `fun logout(): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Log out the previously logged in user |
| [observeChatList](observe-chat-list.md) | `fun observeChatList(callback: (`[`List`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-list/index.html)`<`[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`>) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Observe new incoming chats. This api is idempotent. Only one first callback is respected until clearChatListObserver is called. |
| [recordAudioForPrimaryWalkieTalkieConversation](record-audio-for-primary-walkie-talkie-conversation.md) | `fun recordAudioForPrimaryWalkieTalkieConversation(lifecycle: Lifecycle, audioRecorderCallbacks: `[`AudioRecorderCallbacks`](../../com.rebelvox.voxersdk.conversation/-audio-recorder-callbacks/index.md)`, messageCallbacks: `[`MessageCallbacks`](../../com.rebelvox.voxersdk.conversation/-message-callbacks/index.md)`, stopRecordingCallback: (conversation: `[`Conversation`](../../com.rebelvox.voxersdk.conversation/-conversation/index.md)`) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Start audio recording for conversation with primary walkie talkie mode enabled The app must be given permission to record audio before calling this function |
| [startConversationWith](start-conversation-with.md) | `fun startConversationWith(otherUserId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, lifecycle: Lifecycle, callback: `[`Voxer.ConversationStarterCallback`](-conversation-starter-callback/index.md)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Start a new [Conversation](../../com.rebelvox.voxersdk.conversation/-conversation/index.md) with other user |

### Companion Object Functions

| Name | Summary |
|---|---|
| [getInstance](get-instance.md) | `fun getInstance(application: `[`Application`](https://developer.android.com/reference/android/app/Application.html)`, coroutineScope: CoroutineScope = GlobalScope, enablePlayAudioInBackground: `[`Boolean`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html)` = false): `[`Voxer`](./index.md)<br>Get the Voxer SDK instance |
