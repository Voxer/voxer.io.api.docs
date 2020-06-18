[voxersdk](../../../index.md) / [com.rebelvox.voxersdk.conversation](../../index.md) / [Conversation](../index.md) / [MessagePlaybackListener](./index.md)

# MessagePlaybackListener

`interface MessagePlaybackListener`

Callback to signal different states of Audio playback

### Functions

| Name | Summary |
|---|---|
| [onError](on-error.md) | `open fun onError(): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html) |
| [onPaused](on-paused.md) | `abstract fun onPaused(): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Given audio is paused or hasn't started playing |
| [onPlaying](on-playing.md) | `abstract fun onPlaying(): `[`Unit`](https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-unit/index.html)<br>Given audio is playing |
