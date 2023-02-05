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

## Alert buttons with different roles

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


