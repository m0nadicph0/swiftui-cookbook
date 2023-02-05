# Alerts

## Basic Alert

```swift
struct ContentView: View {
    @State private var alertVisible:Bool = false
    
    var body: some View {
        VStack {

            Button("Show Alert") {
                alertVisible = true
            }.alert("Important !", isPresented: $alertVisible) {
                Button("OK") {
                    alertVisible = false
                }
            }
        }.padding()
    }
}
```

## Alert buttons with different roles

```swift
struct ContentView: View {
    @State private var alertVisible:Bool = false
    
    var body: some View {
        VStack {

            Button("Show Alert") {
                alertVisible = true
            }.alert("Important !", isPresented: $alertVisible) {
                
                Button("OK") {
                    alertVisible = false
                }
                Button("Cancel", role: .cancel) {
                    alertVisible = false
                }
                Button("Delete", role: .destructive) {
                    alertVisible = false
                }
            } message: {
                Text("Please read this !")
            }
        }.padding()
    }
}
```
## Alert with TextField

```swift
struct ContentView: View {
    @State private var alertVisible = false
    @State private var licenseKey = ""
    var body: some View {
        Button("Show Alert") {
            alertVisible.toggle()
        }
        .alert("About App", isPresented: $alertVisible) {
            TextField("License Key", text: $licenseKey)
            Button("OK") {
                print("You entered \(licenseKey)")
            }
        } message: {
            Text("Enter license key here.")
        }
        
    }

}
```



