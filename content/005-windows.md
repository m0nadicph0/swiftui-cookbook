# Windows

## Disable window resizability
<details>
  <summary>Expand</summary>
Add a frame with fixed width and height

```swift
struct ContentView: View {
    
    @State private var isPresented:Bool = false
    @State private var agreed:Bool = false
    
    var body: some View {
        VStack{
            Image(systemName: "globe.americas.fill")
                .foregroundColor(.blue)
                .font(.system(size: 80))
                .padding()
            
            Text("Hello World !!")
            
        }.frame(width: 400, height: 300)
        
    }
    
}
```
Set window resizability limited to content size

```swift
@main
struct UIKitchenSinkApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }.windowResizability(.contentSize)
    }
}
```
</details>

## Hide window titlebar and make entire window background as white
<details>
  <summary>Expand</summary>

Set window style `.hiddenTitleBar` in the `WindowGroup`

```swift
@main
struct TodoApp: App {
    var body: some Scene {
        WindowGroup {
            ContentView()
        }.windowStyle(.hiddenTitleBar)
    }
}
```  
In the `ContentView` set the background

```
struct ContentView: View {
    var body: some View {
        VStack {
            // ...
        }
        .background {
            Rectangle()
                .fill(.white)
                .ignoresSafeArea()
        }
    }
}  
```
</details>

## Close a macOS SwiftUI application when the last window is closed by the user
<details>
  <summary>Expand</summary>

Create an app delegate class
```swift
class AppDelegate: NSObject, NSApplicationDelegate {
    func applicationShouldTerminateAfterLastWindowClosed(_ sender: NSApplication) -> Bool {
        return true
    }
}
```

Add a property wrapper for the app class
  
```
@main
struct SwiftUIApp: App {
    @NSApplicationDelegateAdaptor(AppDelegate.self) var appDelegate
    
    var body: some Scene {
        WindowGroup {
            ContentView()
        }
    }
}
```
</details>

## Disable show all tabs menu

<details>
  <summary>Expand</summary>
  
```
@main
struct SwiftUIApp: App {
    @NSApplicationDelegateAdaptor(AppDelegate.self) var appDelegate
    
    var body: some Scene {
        WindowGroup {
            ContentView()
                ContentView()
                .onAppear{
                    NSWindow.allowsAutomaticWindowTabbing = false
                }
    
        }
    }
}
```
