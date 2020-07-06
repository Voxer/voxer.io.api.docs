# Voxer iOS SDK v0.3

## Requirements
- A deployment target of iOS 11 and above is required
- Xcode 11

## Features
- Login with any users using App ID and App Secret
- Users can send and receive text & audio messages
- For the receiver to receive and play live audio message, it has to be on the conversation screen.

## VoxerKitDemo App
To run the VoxerKitDemo, simply open "VoxerKitDemo.xcworkspace" with Xcode and select "VoxerKitDemo" target to run it on the simulator.

## Xcode Setup
The VoxerKit framework is a fat framework that contains both real iOS device and simulator architecture. They means you can use this framework to run on both physical device and simulator. 

However, when you submit your app to the App Store, you have to strip the VoxerKit framework simulator architecture. Otherwise, the App Store will reject your app. 

1. Download the VoxerKit.framework
2. Add the VoxerKit.framework to your Xcode project. 
3. Under your project "General -> Targets -> Frameworks, Libraries, and Embedded Content", make sure VoxerKit.framework is on the list and "Embed & Sign" is selected. 
4. Go to your project "Build Settings -> Enable Bitcode" and set it to NO.
5. Add a script to strip the VoxerKit.framework simulator architecture. Go to your target's "Build Phases" and add a "New Run Script Phases". Add the following script: 

```
# Don't run this script if it's not a release configuration
if [ "${CONFIGURATION}" != "Release" ]; then
    exit 0
fi

APP_PATH="${TARGET_BUILD_DIR}/${WRAPPER_NAME}"

# Find VoxerKit.framework and remove the simulator architecture.
find "$APP_PATH" -name 'VoxerKit.framework' -type d | while read -r FRAMEWORK
do
    FRAMEWORK_EXECUTABLE_NAME=$(defaults read "$FRAMEWORK/Info.plist" CFBundleExecutable)
    FRAMEWORK_EXECUTABLE_PATH="$FRAMEWORK/$FRAMEWORK_EXECUTABLE_NAME"
    echo "Executable is $FRAMEWORK_EXECUTABLE_PATH"

    EXTRACTED_ARCHS=()

    for ARCH in $ARCHS
    do
        echo "Extracting $ARCH from $FRAMEWORK_EXECUTABLE_NAME"
        lipo -extract "$ARCH" "$FRAMEWORK_EXECUTABLE_PATH" -o "$FRAMEWORK_EXECUTABLE_PATH-$ARCH"
        EXTRACTED_ARCHS+=("$FRAMEWORK_EXECUTABLE_PATH-$ARCH")
    done

    echo "Merging extracted architectures: ${ARCHS}"
    lipo -o "$FRAMEWORK_EXECUTABLE_PATH-merged" -create "${EXTRACTED_ARCHS[@]}"
    rm "${EXTRACTED_ARCHS[@]}"

    echo "Replacing original executable with thinned version"
    rm "$FRAMEWORK_EXECUTABLE_PATH"
    mv "$FRAMEWORK_EXECUTABLE_PATH-merged" "$FRAMEWORK_EXECUTABLE_PATH"
done
```

## Integration Programming Guide

### Initialize Voxer SDK
```
let voxer: Voxer = Voxer(isBackgroundAudioEnable: true)
```

### Log in to the Voxer network
You can get the App ID and App Secret from the Voxer developer portal.
```
voxer.loginWith(username: username, appId: appId, appSecret: appSecret) { [weak self] response in
    if response == .success {
        print ("Login suceeded")
    } else {
        print ("Login failed")
    }
}
```

### Start a conversation with another user
```
voxer.startConversation(with: "bob@localhost") { conversation in
    if conversation != nil {
        print("Successfully started a conversation.")
    }
}
```
 
### Send a text message
```
conversation.send(text:"Hello Bob!")
```

### Send an audio message on voxer network
#### Start recording an audio message
```
conversation.startRecording()
```

#### End recording an audio message
```
conversation.stopRecording()
```

### Message Management
iOS VoxerKit uses Core Data to store and manage message updates

#### Fetch all messages
This code snippet assuming you are using a UITableView.
```
let messageFRC = self.conversation?.getMessageFetchedResultsController()
messageFRC.delegate = self
do {
    try self.messageFRC.performFetch()
} catch let error as NSError {
    print("Failed to fetch messages: " + error.localizedDescription)
}

func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    let message = self.messageFRC.object(at: indexPath)
}
```

#### Listen to message changes to the conversation
You will need to implement `NSFetchedResultsControllerDelegate`:
```
func controllerWillChangeContent(_ controller: NSFetchedResultsController<NSFetchRequestResult>) {
    self.tableView.beginUpdates()
}

func controllerDidChangeContent(_ controller: NSFetchedResultsController<NSFetchRequestResult>) {
    self.tableView.endUpdates()
}

func controller(_ controller: NSFetchedResultsController<NSFetchRequestResult>, didChange anObject: Any, at indexPath: IndexPath?, for type: NSFetchedResultsChangeType, newIndexPath: IndexPath?) {
    
    guard let index = indexPath ?? (newIndexPath ?? nil) else { return }
    
    switch type {
    case .insert:
        guard let message = anObject as? Message else { return }
        tableView.insertRows(at: [index], with: .top)
        if message.contentType == .audio {
            self.newMessageIndex = index
        }
    default:
        // Handle other cases as needed.
        return
    }
}
```

### Log out of the Voxer network
```
voxer.logout()
```

## APIs Documentation

API documentation can be found here: docs/index.html

## Debugging
### Using local stand alone server for development 
Talk to Voxer dev team if you want more details on how to run a local stand alone server.

To use a local stand alone server, you can add an environment variable in your app launch argument. 

Go to your Xcode project scheme; select "Run" and then select the "Arguments" tab. 

Under "Environment Variables" section; add "localhost_ip" as the Name and set your localhost IP as the Value. Make sure to select the checkbox. 

That's it! Now when you run your app, it will try to connect to the local stand alone server instead of the production server. 
