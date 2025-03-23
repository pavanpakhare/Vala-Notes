# Vala Programming Language Notes

## 1. Overview
- Vala is a programming language developed by GNOME.
- It is designed to make GTK development easier while maintaining high performance.
- Syntax is similar to C# but compiles to C for efficiency.

## 2. Features
- Object-oriented programming (OOP) support.
- Memory management with reference counting (like GObject).
- Direct integration with C libraries.
- No need for a runtime or virtual machine.

## 3. Compilation & Execution
- Vala compiles to C, which is then compiled with GCC or Clang.
- Example compilation:
  ```sh
  valac myprogram.vala
  ```

## 4. Basic Syntax

### Hello World Example
```vala
void main() {
    print("Hello, Vala!\n");
}
```

### Variables & Data Types
```vala
int age = 25;
string name = "Vala";
double pi = 3.14;
bool is_cool = true;
```

### Functions
```vala
int add(int a, int b) {
    return a + b;
}

void main() {
    int result = add(5, 10);
    print("Sum: %d\n", result);
}
```

### Classes & Objects
```vala
class Person {
    public string name;
    public int age;

    public Person(string name, int age) {
        this.name = name;
        this.age = age;
    }

    public void introduce() {
        print("Hi, I'm %s and I'm %d years old.\n", name, age);
    }
}

void main() {
    var p = new Person("Alice", 30);
    p.introduce();
}
```

## 5. Memory Management
- Uses GObject's reference counting.
- No manual memory management like in C.
- `weak` references avoid circular dependencies.

## 6. Signals and Callbacks
```vala
class Button : Object {
    public signal void clicked();

    public void press() {
        clicked();
    }
}

void on_button_click() {
    print("Button clicked!\n");
}

void main() {
    var btn = new Button();
    btn.clicked.connect(on_button_click);
    btn.press();
}
```

## 7. GTK Integration
- Vala is primarily used for GTK-based GUI applications.
- Example GUI window with GTK:
```vala
int main(string[] args) {
    Gtk.init(ref args);

    var window = new Gtk.Window();
    window.title = "Vala GTK App";
    window.set_default_size(400, 300);
    window.destroy.connect(Gtk.main_quit);

    window.show_all();
    Gtk.main();

    return 0;
}
```

## 8. Useful Commands
- Compile with debugging:
  ```sh
  valac --debug myprogram.vala
  ```
- Generate a C file:
  ```sh
  valac -C myprogram.vala
  ```

## 9. Pros & Cons

### Pros:
✔ High performance (compiles to C).  
✔ Clean and modern syntax.  
✔ Great for GTK applications.  
✔ No runtime dependencies.  

### Cons:
✖ Smaller community compared to C, C++, or Java.  
✖ Mainly focused on GNOME and Linux development.  
✖ Requires GObject for OOP.  

