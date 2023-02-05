# Sheet

## Basic

```
struct ContentView: View {
    
    @State private var isPresented:Bool = false
    @State private var agreed:Bool = false
    
    var body: some View {
        Image(systemName: agreed ? "checkmark.seal.fill": "xmark.seal.fill").font(.largeTitle)
            .foregroundColor(agreed ? .green : .red )
        
        Button("Show Sheet") {
            isPresented.toggle()
        }
        .sheet(isPresented: $isPresented) {
            VStack {
                Text("License Agreement")
                    .font(.title)
                Text("Terms and conditions go here.")
                .padding(50)
                HStack{
                    Button("Disagree"){
                        agreed = false
                        isPresented.toggle()
                    }
                    Button("Agree"){
                        agreed = true
                        isPresented.toggle()
                    }.buttonStyle(.borderedProminent)
                }
            }.padding()
        }
        
        
    }
    
}
```
