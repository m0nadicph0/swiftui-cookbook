# Buttons

## Basic button

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

## Button Styles

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

## Using Tint

<img width="259" alt="tint" src="https://user-images.githubusercontent.com/123083726/216804536-b6267fc9-cc23-4a1a-b8d5-b134b2e58436.png">

```
struct ContentView: View {
    var body: some View {
        VStack {
            Button("Borderless Red") { }
                .buttonStyle(.borderless)
                .tint(.red)
                .padding()
            Button("Bordered Prominent Red") { }
                .buttonStyle(.borderedProminent)
                .tint(.red)
                .padding()
        }
        .padding()
    }
}
```

## Image buttons
<img width="360" alt="img-buttons" src="https://user-images.githubusercontent.com/123083726/216804733-0acbe9f3-cc3a-4b5d-af93-ff41bca050ac.png">

```
struct ContentView: View {
    var body: some View {
        HStack {
            Button {
                print("edited")
            } label: {
                Image(systemName: "square.and.pencil.circle.fill")
                    .foregroundColor(.mint)
            }
            
            Button {
                print("deleted")
            } label: {
                Image(systemName: "trash.circle.fill")
                    .foregroundColor(.red)
            }
        }
        .padding()
    }
}
````

## Buttons with image and text

<img width="183" alt="btn-with-label" src="https://user-images.githubusercontent.com/123083726/216805178-debe12e8-d36a-44c8-9de8-59418686e449.png">


```
struct ContentView: View {
    var body: some View {
        VStack {
            HStack {
                Button {
                    print("edited")
                } label: {
                    Label("Edit", systemImage: "square.and.pencil.circle.fill")
                        .foregroundColor(.white)
                }.buttonStyle(.borderedProminent)
                
                Button {
                    print("deleted")
                } label: {
                    Label("Delete", systemImage: "trash.circle.fill")
                        .foregroundColor(.white)
                }.buttonStyle(.borderedProminent).tint(.red)
            }
            
            
            
            
            HStack {
                Button {
                    print("edited")
                } label: {
                    Label("Edit", systemImage: "square.and.pencil.circle.fill")
                        .foregroundColor(.blue)
                }
                
                Button {
                    print("deleted")
                } label: {
                    Label("Delete", systemImage: "trash.circle.fill")
                        .foregroundColor(.red)
                }
            }
        }
        .padding()
    }
}
```
## Custom Buttons

<img width="169" alt="custom" src="https://user-images.githubusercontent.com/123083726/216806206-4d039930-a5d9-4b69-8ce1-17d3a0f5abb8.png">

```
struct ContentView: View {
    var body: some View {
        VStack {

            Button {
                print("Button was tapped")
            } label: {
                Text("Tap me!")
                    .padding()
                    .foregroundColor(.white)
                    .background(.red)
                    .clipShape(Capsule())
                    .shadow(color: .gray, radius: 2, x: 0, y: 2)
                    .padding()
            }.buttonStyle(.borderless)
            
            Button{
                print("Button was tapped")
            }label:{
                Text("Tap Me !")
                    .font(.system(size: 17))
                    .fontWeight(.bold)
                    .foregroundColor(.green)
                    .padding()
                    .background(
                        RoundedRectangle(cornerRadius: 25)
                            .fill(Color.white)
                            .shadow(color: .gray, radius: 2, x: 0, y: 2)
                )
                .padding()
            }.buttonStyle(.borderless)
            
        }
    }
}
```
## Custom button styles
![custom-button-style](https://user-images.githubusercontent.com/123083726/216807585-78c25c6d-562c-478d-9948-7fbde00c87dd.gif)

```
struct BlueButton: ButtonStyle {
    func makeBody(configuration: Configuration) -> some View {
        configuration.label
            .padding()
            .background(Color(red: 0, green: 0, blue: 0.5))
            .foregroundColor(.white)
            .clipShape(Capsule())
            .scaleEffect(configuration.isPressed ? 1.1 : 1)
            .animation(.easeOut(duration: 0.05), value: configuration.isPressed)
    }
}

struct GrowingButton: ButtonStyle {
    func makeBody(configuration: Configuration) -> some View {
        configuration.label
            .padding()
            .background(.blue)
            .foregroundColor(.white)
            .clipShape(RoundedRectangle(cornerRadius: 10))
            .scaleEffect(configuration.isPressed ? 1.1 : 1)
            .animation(.easeOut(duration: 0.05), value: configuration.isPressed)
    }
}



struct ContentView: View {
    var body: some View {
        VStack {

            Button("Click Me !") {
                print("button clicked...")
            }.buttonStyle(BlueButton())
            
            Button("Click Me !") {
                print("button clicked...")
            }.buttonStyle(GrowingButton())

        }.padding()
    }
}
```


