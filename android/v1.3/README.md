# Voxer Android SDK v1.3

### Feature description

1. Every client will be provided with unique appId and appSecret. These two values will be needed to initialize voxer sdk in their apps.
2. Any user can login using a unique user id. Users can the start chat with any other user as long they know the user id of the other user.  
3. Users can send audio and text messages. Sdk provides different callbacks to signal whether message has been successfully sent, waiting to be sent or failed to send. Users can resend the failed message after sdk signals failures to send. Every time user sends a new message or resends failed message, sdk tries multiple times in background before returning it as failed message. 
4. Users can receive live audio messages, pre-recorded audio messages and text messages.
5. **Walkie Talkie Feature (Play)** After the user starts the chat with any user by explicitly calling start chat, any incoming live audio message will be played out loud regardless of whether app is in background or foreground. SDK will continue to play live audio outloud from there on until user explicitly calls logout.
6. **Walkie Talkie Feature (Record)** Users can record an audio to a chat using an external button. User has to mark the chat as primary to enable this feature. At any given time only one chat can be marked as primary. If user marks a chat as primary while some other chat is already marked as primary, sdk overrides the older selection with the latest selection. 
7. **Audio Focus** Sdk respects audio focus rules of the ecosystem. It stops audio playback if user picks up a call. It lowers the volume upon loosing audio focus for brief period of time and restores the audio playback volume upon regaining the focus. It also stops audio playback upon completely loosing audio focus. Sdk only starts audio recording if no phone call is in progress. 
8. **Audio playback routing** Sdk can route audio through bluetooth headset(supports HFP or A2DP profile), wired headset, earpiece or phone speaker. User can explicitly choose to play from either earpiece or speaker, if neither wired headset or bluetooth headset is connected.

9. **Audio mic routing** Sdk can record audio from phone mic, wired headset or bluetooth headset. Sdk automically switch to wired headset or bluetooth headset if any one of them is connected. Once the user disconnects external mic, the sdk defaults to phone mic. 
### Initialize Voxer SDK 

#### With default feature - play audio in background enabled

```
Voxer.getInstance(application)
```

#### With default feature - play audio in background disabled

```
Voxer.getInstance(application, enablePlayAudioInBackground = false)
```


Please provide record permission to allow Voxer to record audio

```
<uses-permission android:name="android.permission.RECORD_AUDIO" />
```

### Log into Voxer network 

```
Voxer.getInstance(application).login (username,appId, appSecret) 
{ success ->
   if (success) { //handle successfull login }
   else         { //handle login failure }
}
 ```
 
 ### Log out of Voxer network
 
 ```
 GlobalScope.launch { Voxer.getInstance(application).logout() }
 
 ```

### Initialize Voxer SDK and start a new chat with the given user

```
voxer.startChatWith(otherUserId, lifecycle, chatStarterCallback)
```

Here is the code snippet which. shows sample chatStarterCallback : 

```
override fun onChatStarted(chat: Chat) {
    lifecycleScope.launch(Dispatchers.Main) {
            //Initialize UI
            //Refresh List
            //Listen for new incoming messages
        }
    }

override fun onError(e: Error) {
       //Display appropriate message to the user
    }
```
    
 
 ### Send text message on voxer network
 
 ```
 chat.sendTextMessage(text, messageCallback)
 ```
 
 Here is the code snippet which shows how to use the above api with an UI element
 
 ```
 btnSendMessage.setOnClickListener {
     val messageBody = etStartTyping.text.toString()
     sendTextMessage(messageBody) {
          btnSendMessage.hideKeyboard()
     }
     etStartTyping.setText("")
 }
 ```

### Send Audio message on voxer network

```
chat.startRecording( onRecordingStarted = { // refresh the list of messages },
            messageCallbacks = MessageCallbacks())
```

User can stop sending audio message using the following code snippet 

```
chat.stopRecording()
```

### Listen to message updates

```
chat.subscribeToNewMessages { message ->
            addNewMessageToList(message)
        }
```

User can use following code snippet as reference when designing their list adapter : 

```
class MessageInteractorInterfaceImpl(private val chat: Chat,
                                     private val refreshMessageListCallback: (List<MessageUser>) -> Unit) : MessageInteractorInterface{
    override fun playMessage(messageUser: MessageUser,listener: Conversation.MessagePlaybackListener) {
        chat.playMessage(messageUser,listener)
    }

    override fun pauseMessage(messageUser: MessageUser) {
        chat.pauseMessage(messageUser)
    }

    override fun removePlaybackListenerForMessage(messageUser: MessageUser) {
        chat.removeListenerForMessage(messageUser)
    }

    override fun isMessageBeingRecorded(messageUser: MessageUser): Boolean {
        return chat.isMessageBeingRecorded(messageUser)
    }

    override fun refreshMessages() {
        chat.getMessages { list ->
            refreshMessageListCallback(list)
        }
    }
}
```
### Walkie talkie feature usage
#### Mark chat as primary
```
voxer.enableWalkieTalkie(chatId!!)
```
#### Disable walkie talkie feature for a given chat
```
voxer.disableWalkieTalkie(chatId)
```
#### Start recording for primary chat
```
voxer.toggleAudioForWalkieTalkieChat(lifecycle = this.lifecycle,
                        audioRecorderCallbacks = getSampleAudioRecorderCallbacks(context = this),
                        messageCallbacks = SampleMessageCallback(context = this))
```

### Get list of chats
```
voxer.getInstance(application).getChats(){ chatNames: List<String> ->
//TODO: UPDATE UI
}
```

### Observe list of chats
User can use following code snippet as reference to observe list of chats : 

```
voxer.observeChatList {chatNames: List<String> ->
chatNames: List<String> ->
//TODO: UPDATE UI
}
```

Client should stop observing the list using following call : 
```
voxer.clearChatListObserver()
```

### APIs

Description of the  APIs showcased above can be found [here](docs/voxersdk/index.md)
