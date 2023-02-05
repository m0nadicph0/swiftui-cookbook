# Alerts

## Basic Alert

```
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


