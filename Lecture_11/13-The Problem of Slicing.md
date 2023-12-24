[//]: # (### The Problem of Slicing)

What happens when a programmer does the following?

```cpp
Derived objDerived;
Base objectBase = objDerived;
```

Or, alternatively, what if a programmer does this?

```cpp
void UseBase(Base input);
Derived objDerived;
UseBase(objDerived); // copy of objDerived will be sliced and sent
```

In both cases, an object of type `Derived` is being copied into another object of type `Base`, either explicitly via assignment or by being passed as an argument. What happens in these cases is that the compiler copies only the Base part of `objDerived` and not the complete object. The information contained by the data members belonging to `Derived` is lost in the process.

#### Example

   ```cpp
   class Base {
   public:
       int baseData;
   };

   class Derived : public Base {
   public:
       int derivedData;
   };

   int main() {
       Derived derivedObj;
       derivedObj.baseData = 10;
       derivedObj.derivedData = 20;

       Base baseObj = derivedObj;  // Slicing occurs here
       // Now, baseObj has only the Base part of derivedObj
   }
   ```

**Result:**

- After the assignment, `baseObj` contains only the `baseData` part of the `derivedObj`.
- The `derivedData` from `derivedObj` is lost in `baseObj` due to slicing.

**Avoiding Slicing:**

- Instead of assigning objects directly, use pointers or references to base classes to preserve the complete derived class object.
