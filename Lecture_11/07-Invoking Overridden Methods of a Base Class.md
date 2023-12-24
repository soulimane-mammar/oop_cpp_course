[//]: # (### Invoking Overridden Methods of a Base Class)

In the previous code, we saw an example of the derived class `Tuna` overriding the `Swim()` function in `Fish` by implementing its version of the function. Essentially:

```cpp
Tuna myDinner; 
myDinner.Swim(); // will invoke Tuna::Swim()
```

If we want to invoke `Fish::Swim()`  via main(), we need to use the scope resolution operator (`::`) in the following way:

```cpp
myDinner.Fish::Swim(); // invokes Fish::Swim() using instance of Tuna
```
