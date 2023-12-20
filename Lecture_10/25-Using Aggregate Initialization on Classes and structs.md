[//]: # (### Using Aggregate Initialization on Classes and structs)

Aggregate initialization allows initializing the members of a class or struct using a concise syntax by enclosing the initial values within curly braces `{}`. This feature is available in C++ and allows you to initialize all or some members of an aggregate (which includes arrays, classes, and structs) in a single line.

#### Example Using Aggregate Initialization

```cpp
#include <iostream>
using namespace std;

// Struct definition
struct Point {
    int x;
    int y;
    int z;
};

// Class definition
class Rectangle {
public:
    int width;
    int height;
};


int main() {
    // Aggregate initialization for struct
    Point p1 = {10, 20, 30};
    //or
    //Point p1 {10, 20, 30};

    cout << "Point Coordinates: " << p1.x << ", " << p1.y << ", " << p1.z << endl;

    // Aggregate initialization for class
    Rectangle rect = {5, 10};

    cout << "Rectangle Width: " << rect.width << ", Height: " << rect.height << endl;


    return 0;
}
```

In this example:

- The `Point` struct represents a point in three-dimensional space with `x`, `y`, and `z` coordinates.
- Using aggregate initialization, the `p1` object of type `Point` is initialized with values `{10, 20, 30}` for its members `x`, `y`, and `z`.
- The `Rectangle` class represents a rectangle with `width` and `height`.
- Using aggregate initialization, the `rect` object of type `Rectangle` is initialized with values `{5, 10}` for its members `width` and `height`.

#### Restrictions and Considerations

- Aggregate initialization applies to:
  - classes/structs with public non-static data members and no user-defined constructors, destructor, or private/protected non-static data members or virtual member functions..
  - classes that do not utilize inheritance, except for public inheritance without private, protected, or virtual inheritance.
- Initialization must be in the order of declaration
- If the class/struct doesn't meet these conditions, you may encounter compile-time errors related to aggregate initialization.
