[//]: # (### Operators That Cannot Be Overloaded)

C++ gives you a lot of flexibility in customizing the behavior of operators and making your classes easy to use. However, it does not allow you to change or alter the behavior of some operators that are expected to perform consistently. The operators that cannot be redefined are shown in following Table

| Operators                          | Description                                                                           |
|------------------------------------|---------------------------------------------------------------------------------------|
| Scope Resolution (`::`)               | Accesses namespace and class members                                                   |
| Member Selection (`.`)  | Accesses members of objects                      |
| Member Selection (`.*`)  | Member access through pointer to member                      |
| Conditional (`?:`)                   | Ternary conditional operator                                                          |
| `sizeof`                             | Determines the size of objects or types                                               |
