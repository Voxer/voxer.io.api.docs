[voxersdk](../../index.md) / [com.rebelvox.voxersdk.chat](../index.md) / [Chat](./index.md)

# Chat

`class Chat`

Represents Chat betweeen two users.
This class allows the sdk users to send &amp; receive text and audio messages

### Types

| Name | Summary |
|---|---|
| [MessagePlaybackListener](-message-playback-listener/index.md) | `interface MessagePlaybackListener`<br>Callback to signal different states of Audio playback |

### Functions

| Name | Summary |
|---|---|
| [destroy](destroy.md) | `fun destroy(): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Clean up [Chat](./index.md) resources when user navigates away from chat page |
| [enableAutomaticAudioRouting](enable-automatic-audio-routing.md) | `fun enableAutomaticAudioRouting(): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Enable automatic audio routing option for a given user |
| [enableEarpieceMode](enable-earpiece-mode.md) | `fun enableEarpieceMode(): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Do not play audio out loud |
| [enableSpeakerMode](enable-speaker-mode.md) | `fun enableSpeakerMode(): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Route audio via speaker |
| [getCurrentAudioRoutingOption](get-current-audio-routing-option.md) | `fun getCurrentAudioRoutingOption(): AudioPlaybackRoutingOption`<br>Force headset mode on and save relevant state data if needed |
| [getFailedMessageCount](get-failed-message-count.md) | `fun getFailedMessageCount(): `[`SyncData`](../../com.rebelvox.voxersdk.synchronization/-sync-data/index.md)<br>Are messages waiting to be retried |
| [getMessages](get-messages.md) | `fun getMessages(callback: (`[`List`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin.collections/-list/index.html)`<MessageUser>) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Get the list of new messages |
| [getName](get-name.md) | `fun getName(callback: (`[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Get name of the [Chat](./index.md) |
| [pauseMessage](pause-message.md) | `fun pauseMessage(messageUser: MessageUser): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Pause the audio playback for the given [messageUser](pause-message.md#com.rebelvox.voxersdk.chat.Chat$pauseMessage(com.rebelvox.dataaccessor.messageAccessor.MessageUser)/messageUser) |
| [playMessage](play-message.md) | `fun playMessage(messageUser: MessageUser, listener: `[`Chat.MessagePlaybackListener`](-message-playback-listener/index.md)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Play a given audio message |
| [removeListenerForMessage](remove-listener-for-message.md) | `fun removeListenerForMessage(messageUser: MessageUser): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Remove [MessagePlaybackListener](-message-playback-listener/index.md) for message |
| [retryAllFailedMessages](retry-all-failed-messages.md) | `fun retryAllFailedMessages(): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Retry sending all failed messages |
| [retryFailedMessage](retry-failed-message.md) | `fun retryFailedMessage(messageId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Retry sending failed message |
| [sendTextMessage](send-text-message.md) | `fun sendTextMessage(text: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`, messageCallbacks: `[`MessageCallbacks`](../-message-callbacks/index.md)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Send text message to all the participants of the chat |
| [startRecording](start-recording.md) | `fun startRecording(audioRecorderCallbacks: `[`AudioRecorderCallbacks`](../-audio-recorder-callbacks/index.md)`, messageCallbacks: `[`MessageCallbacks`](../-message-callbacks/index.md)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Start audio recording for this chat. The app must be given permission to record audio before calling this function |
| [stopRecording](stop-recording.md) | `fun stopRecording(): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Stop audio recording for this chat |
| [subscribeToNewMessages](subscribe-to-new-messages.md) | `fun subscribeToNewMessages(onNewMessage: (MessageUser) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Listen for new incoming messages |
