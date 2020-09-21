[voxersdk](../../index.md) / [com.rebelvox.voxersdk](../index.md) / [Voxer](./index.md)

# Voxer

`class Voxer`

Entry point for the Voxer SDK

### Types

| Name | Summary |
|---|---|
| [ChatStarterCallback](-chat-starter-callback/index.md) | `interface ChatStarterCallback`<br>Interface defining callbacks which are called when user of the sdk starts a new chat |

### Functions

| Name | Summary |
|---|---|
| [clearChatListObserver](clear-chat-list-observer.md) | `fun clearChatListObserver(): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Stop observing new chats |
| [createUser](create-user.md) | `fun createUser(username: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, appSecret: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, appId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, firstName: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, lastName: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, avatarUri: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, callback: (`[`Boolean`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html)`) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Create new user in Voxer network |
| [disableWalkieTalkie](disable-walkie-talkie.md) | `fun disableWalkieTalkie(chatId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Disable the chatId for walkie talkie. If the chatId is not enabled for walkie talkie. This method does nothing and false Bool is returned. |
| [enableWalkieTalkie](enable-walkie-talkie.md) | `fun enableWalkieTalkie(chatId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Enable sending audio directly and play received audio automatically. It does not check if the chatId is valid. There can only be one chatId enabled for walkie talkie. If there is already a chatId enabled for walkie talkie, setting a different chatId will overwrite the old chatId. The new chatId will be the one enabled for walkie talkie. The old chatId will be disabled. |
| [getChats](get-chats.md) | `fun getChats(callback: (`[`List`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-list/index.html)`<`[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`>) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Get list of chats |
| [getLoggedInUser](get-logged-in-user.md) | `fun getLoggedInUser(): `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)<br>Get already logged in user |
| [login](login.md) | `fun login(username: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, appSecret: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, appId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, callback: (`[`Boolean`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html)`) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Log into Voxer network |
| [logout](logout.md) | `fun logout(): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Log out the previously logged in user |
| [observeChatList](observe-chat-list.md) | `fun observeChatList(callback: (`[`List`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-list/index.html)`<`[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`>) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Observe new incoming chats. This api is idempotent. Only one first callback is respected until clearChatListObserver is called. |
| [startChatWith](start-chat-with.md) | `fun startChatWith(otherUserId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, lifecycle: Lifecycle, callback: `[`Voxer.ChatStarterCallback`](-chat-starter-callback/index.md)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Start a new [Chat](../../com.rebelvox.voxersdk.chat/-chat/index.md) with other user |
| [toggleAudioForWalkieTalkieChat](toggle-audio-for-walkie-talkie-chat.md) | `fun toggleAudioForWalkieTalkieChat(lifecycle: Lifecycle, audioRecorderCallbacks: `[`AudioRecorderCallbacks`](../../com.rebelvox.voxersdk.chat/-audio-recorder-callbacks/index.md)`, messageCallbacks: `[`MessageCallbacks`](../../com.rebelvox.voxersdk.chat/-message-callbacks/index.md)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Start audio recording for chat with primary walkie talkie mode enabled The app must be given permission to record audio before calling this function |

### Companion Object Functions

| Name | Summary |
|---|---|
| [getInstance](get-instance.md) | `fun getInstance(application: `[`Application`](https://developer.android.com/reference/android/app/Application.html)`, coroutineScope: CoroutineScope = GlobalScope, enablePlayAudioInBackground: `[`Boolean`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-boolean/index.html)` = false): `[`Voxer`](./index.md)<br>Get the Voxer SDK instance |
