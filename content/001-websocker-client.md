# Websocket Client 

Use [Starscream](https://github.com/daltoniam/Starscream) library. 
1. File -> Add Packages -> Find `https://github.com/daltoniam/Starscream.git` -> Add package

2. Add the following code in the `ContentView`

```
import SwiftUI
import Starscream

struct ContentView: View {
    @State private var socket: WebSocket?
    
    var body: some View {
        VStack {
            Image(systemName: "globe")
                .imageScale(.large)
                .foregroundColor(.accentColor)
            Button("Connect") {
                let request = URLRequest(url: URL(string: "ws://localhost:9696/ws")!)
                
                self.socket = WebSocket(request: request)
                self.socket?.onEvent = { event in
                    switch event {
                    case .connected(let headers):
                        print("websocket is connected: \(headers)")
                    case .disconnected(let reason, let code):
                        print("websocket is disconnected: \(reason) with code: \(code)")
                    case .text(let string):
                        print("Received text: \(string)")
                    case .binary(let data):
                        print("Received data: \(data.count)")
                    case .ping(_):
                        break
                    case .pong(_):
                        break
                    case .viabilityChanged(_):
                        break
                    case .reconnectSuggested(_):
                        break
                    case .error(let error):
                        print(error!)
                    case .cancelled:
                        print("cancelled")
                    }
                }
                self.socket?.connect()
            }
        }
        .padding()
        .frame(minWidth: 400, minHeight: 400)
    }
}
```
