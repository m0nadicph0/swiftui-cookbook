# Buttons

## Most basic button

```
Button("Click me") {
  // Do something
}
```

## Button with action

```
struct ContentView: View {
    var body: some View {
        VStack {
            Button("Do something", action: doSomething)
        }
        .padding()
    }
    
    func doSomething() {
        print("Doing something...")
    }
}
```

### Button Styles

<img width="270" alt="button-styles" src="https://user-images.githubusercontent.com/123083726/216801903-52670367-5298-4d97-83b9-09160607a9b7.png">

```
struct ContentView: View {
    var body: some View {
        VStack {
            Button("Default Button") { print("clicked") }
            Button("Plain Button") { print("clicked") }
                .buttonStyle(.plain)
            Button("Bordered Button") { print("clicked") }
                .buttonStyle(.bordered)
            Button("Bordered Prominent Button") { print("clicked") }
                .buttonStyle(.borderedProminent)
            Button("Borderless Button") { print("clicked") }
                .buttonStyle(.borderless)
            Button("Link Button") { print("clicked") }
                .buttonStyle(.link)
        }
        .padding()
    }
}
```
