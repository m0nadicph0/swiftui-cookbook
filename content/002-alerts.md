# Alerts

## Basic Alert
![output](https://user-images.githubusercontent.com/123083726/216807981-5d0eae3a-b87f-41ad-a0d2-2f6cc52a636f.gif)

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
