# game.hpp Documentation

## Index

- [Functions](#functions)
  - [Vectors](#vectors)
  - [Camera](#camera)
  - [Object Declaration](#object-declaration)
  - [Object Movement](#object-movement)
- [Source Code & Modding Guidelines](#source-code--modding-guidelines)
- [List of functions](#list-of-functions)

## Functions

### Vectors

This section covers the Vec2 and Vec3 classes, which represent 2D and 3D vectors, respectively. <br>
These classes provide basic vector arithmetic operations and predefined directional vectors for 3D space <br>
<br>
Class: Vec2 <br>
Description: The Vec2 class represents a vector in 2D space with x and y components. It supports basic vector arithmetic operations such as addition, subtraction, and scalar multiplication. 

```cpp
Vec2(int x, int y) // Creates a 2D vector with specified x and y components.
```
Conversion to Vec3: Vec2 can automatically convert to Vec3. When converted, the z component of the resulting Vec3 is set to 0. <br>
<br>
Class: Vec3
Description: The Vec3 class represents a vector in 3D space with x, y, and z components. It supports vector addition, subtraction, scalar multiplication, <br>
and includes predefined directional vectors for common directions like up, down, left, right, forward, and backward <br>
<br>
Constructors:
```cpp
Vec3(int x, int y, int z) // Creates a 3D vector with specified x, y, and z components.
```
<br>

Predefined Directions:
```cpp
vector.up() // Returns a vector (0, 1, 0) representing the upward direction.
vector.down() // Returns a vector (0, -1, 0) representing the downward direction.
vector.left() // Returns a vector (-1, 0, 0) representing the left direction.
vector.right() // Returns a vector (1, 0, 0) representing the right direction.
vector.forward() // Returns a vector (0, 0, 1) representing the forward direction.
vector.backward() // Returns a vector (0, 0, -1) representing the backward direction.
vector.zero() // Returns a vector (0, 0, 0) representing the origin or no movement.
```

Example:
```cpp
Vec2 v1(3, 4);
Vec3 v2(1, 2, 3);
Vec3 result = v1 + v2 + vec3.up; // result is (4, 7, 3)
```
<br>
<br>



**NOTE:
While the Vec2 class is available for convenience when working with 2D vectors, all vector operations and parameters in the system ultimately use Vec3. <br> 
Whenever a Vec2 is used, it is automatically converted into a Vec3 by setting the z component to 0.** <br> 


### List of functions


