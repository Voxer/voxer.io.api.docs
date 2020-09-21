[voxersdk](../../index.md) / [com.rebelvox.voxersdk](../index.md) / [Voxer](index.md) / [recordAudioForPrimaryWalkieTalkieConversation](./record-audio-for-primary-walkie-talkie-chat.md)

# recordAudioForPrimaryWalkieTalkieConversation

`fun recordAudioForPrimaryWalkieTalkieConversation(lifecycle: Lifecycle, audioRecorderCallbacks: `[`AudioRecorderCallbacks`](../../chat/-audio-recorder-callbacks/index.md)`, messageCallbacks: `[`MessageCallbacks`](../../chat/-message-callbacks/index.md)`, stopRecordingCallback: (chat: `[`Conversation`](../../chat/-chat/index.md)`) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)`): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)

Start audio recording for chat with primary walkie talkie mode enabled
The app must be given permission to record audio before calling this function

### Parameters

`lifecycle` -

`messageCallbacks` -

`audioRecorderCallbacks` -

`stopRecordingCallback` - 