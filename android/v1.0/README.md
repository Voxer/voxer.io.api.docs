# Voxer Android SDK v0.5

### Feature description

1. Every client will be provided with unique appId and appSecret. These two values will be needed to initialize voxer sdk in their apps.
2. Any user can login using a unique user id. Users can the start chat with any other user as long they know the user id of the other user.  
3. Users can send audio and text messages. Sdk provides different callbacks to signal whether message has been successfully sent, waiting to be sent or failed to send. Users can resend the failed message after sdk signals failures to send. Every time user sends a new message or resends failed message, sdk tries multiple times in background before returning it as failed message. 
4. Users can receive live audio messages, pre-recorded audio messages and text messages.
5. **Walkie Talkie Feature (Play)** After the user starts the chat with any user by explicitly calling start conversation, any incoming live audio message will be played out loud regardless of whether app is in background or foreground. SDK will continue to play live audio outloud from there on until user explicitly calls logout.
6. **Walkie Talkie Feature (Record)** Users can record an audio to a conversation using an external button. User has to mark the conversation as primary to enable this feature. At any given time only one conversation can be marked as primary. If user marks a conversation as primary while some other conversation is already marked as primary, sdk overrides the older selection with the latest selection. 
7. **Audio Focus** Sdk respects audio focus rules of the ecosystem. It stops audio playback if user picks up a call. It lowers the volume upon loosing audio focus for brief period of time and restores the audio playback volume upon regaining the focus. It also stops audio playback upon completely loosing audio focus. Sdk only starts audio recording if no phone call is in progress. 

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

### Initialize Voxer SDK and start a new conversation with the given user

```
voxer.startConversationWith(otherUserId, lifecycle, conversationStarterCallback)
```

Here is the code snippet which. shows sample conversationStarterCallback : 

```
override fun onConversationStarted(conversation: Conversation) {
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
 conversation.sendTextMessage(text, messageCallback)
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
conversation.startRecording( onRecordingStarted = { // refresh the list of messages },
            messageCallbacks = MessageCallbacks())
```

User can stop sending audio message using the following code snippet 

```
conversation.stopRecording()
```

### Listen to message updates

```
conversation.subscribeToNewMessages { message ->
            addNewMessageToList(message)
        }
```

User can use following code snippet as reference when designing their list adapter : 

```
class MessageInteractorInterfaceImpl(private val conversation: Conversation,
                                     private val refreshMessageListCallback: (List<MessageUser>) -> Unit) : MessageInteractorInterface{
    override fun playMessage(messageUser: MessageUser,listener: Conversation.MessagePlaybackListener) {
        conversation.playMessage(messageUser,listener)
    }

    override fun pauseMessage(messageUser: MessageUser) {
        conversation.pauseMessage(messageUser)
    }

    override fun removePlaybackListenerForMessage(messageUser: MessageUser) {
        conversation.removeListenerForMessage(messageUser)
    }

    override fun isMessageBeingRecorded(messageUser: MessageUser): Boolean {
        return conversation.isMessageBeingRecorded(messageUser)
    }

    override fun refreshMessages() {
        conversation.getMessages { list ->
            refreshMessageListCallback(list)
        }
    }
}
```
### Walkie talkie feature usage
#### Mark conversation as primary
```
voxer.enablePrimaryWalkieTalkieMode(threadId!!)
```
#### Disable walkie talkie feature for a given conversation
```
voxer.disablePrimaryWalkieTalkieMode(threadId)
```
#### Start recording for primary conversation
```
voxer.recordAudioForPrimaryWalkieTalkieConversation(lifecycle = this.lifecycle,
                        audioRecorderCallbacks = getSampleAudioRecorderCallbacks(context = this),
                        stopRecordingCallback = {
                                conversation ->
                            GlobalScope.launch(Dispatchers.Main) {
                                Snackbar.make(getAnchorView.invoke(),"Conversation to stop: $conversation", Snackbar.LENGTH_LONG).show()
                            }
                        },
                        messageCallbacks = SampleMessageCallback(context = this))
```

### Get list of chats
```
voxer.getInstance(application).getChats(){ threadNames: List<String> ->
//TODO: UPDATE UI
}
```

### Observe list of chats
User can use following code snippet as reference to observe list of chats : 

```
voxer.observeChatList {threadNames: List<String> ->
threadNames: List<String> ->
//TODO: UPDATE UI
}
```

Client should stop observing the list using following call : 
```
voxer.clearChatListObserver()
```

### APIs

Description of the  APIs showcased above can be found [here](voxersdk/index.md)
