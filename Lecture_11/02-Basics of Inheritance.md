[//]: # (### Basics of Inheritance)

In the realm of programming, scenarios often arise where managed components share similar attributes yet vary slightly in their details or behavior. One approach to represent this programmatically involves defining each component as a class, where every class includes all attributes and redefines common ones. Alternatively, employing inheritance enables similar classes to inherit from a base class housing common attributes and functionality. Derived classes can then override this shared functionality to implement distinctive behaviors for each class, which is often the favored method. The figure below visually exemplifies the concept of inheritance within the domain of object-oriented programming.

![Inheritance](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/Lecture_11/inheritance.png?raw=true)

To simplify this concept, consider a base class called `Fish`. This base class is inherited by other classes like `Tuna`, `Carp`, and `Goldfish`. The `Fish` class establishes fundamental fish attributes, such as "can swim," "seawater of freshwater,"  and more. The derived classes, like `Tuna`, `Carp`, and `Goldfish`, inherit these attributes and tailor them according to their specific traits. well as in the fact that it is a saltwater fish.
Thus, `Tuna` and `Carp` inherit common characteristics from a common base class `Fish`, but they specialize the base class attributes to distinguish themselves from each other. This is illustrated in following figure.

![Inheritance Example](https://github.com/soulimane-mammar/oop_cpp_course/blob/main/Lecture_11/fish_tuna_carp.png?raw=true)
