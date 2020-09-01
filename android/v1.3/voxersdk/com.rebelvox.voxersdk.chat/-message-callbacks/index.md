[voxersdk](../../index.md) / [com.rebelvox.voxersdk.chat](../index.md) / [MessageCallbacks](./index.md)

# MessageCallbacks

`interface MessageCallbacks`

### Properties

| Name | Summary |
|---|---|
| [onAudioUploadCompleted](on-audio-upload-completed.md) | `abstract val onAudioUploadCompleted: () -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html) |
| [onAudioUploadFailed](on-audio-upload-failed.md) | `abstract val onAudioUploadFailed: (messageId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html) |
| [onAudioUploadStarted](on-audio-upload-started.md) | `abstract val onAudioUploadStarted: () -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html) |
| [onTextSendingFailed](on-text-sending-failed.md) | `abstract val onTextSendingFailed: (messageId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html) |
| [onTextSendingPending](on-text-sending-pending.md) | `abstract val onTextSendingPending: () -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html) |
| [onTextSentSuccessfully](on-text-sent-successfully.md) | `abstract val onTextSentSuccessfully: () -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html) |
| [onUnkownError](on-unkown-error.md) | `abstract val onUnkownError: (messageId: `[`String`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-string/index.html)`) -> `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html) |
