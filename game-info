# game.hpp Documentation

## Index

- [Functions](#functions)
  - [Vectors](#vectors)
  - [Camera](#camera)
  - [Object Declaration](#object-declaration)
  - [Object Movement](#object-movement)
- [Source Code & Modding Guidelines](#source-code--modding-guidelines)

## Functions

### Vectors

Vectors in the `game.hpp` use a custom structure `v3` defined as follows:

```cpp
struct v3 {
    int x, y, z;
};
```

```cpp
v3 vec3(int x, int y, int z);
```
Explanation:

Parameters:
x: The x-coordinate of the vector.
y: The y-coordinate of the vector.
z: The z-coordinate of the vector.

Returns a v3 structure with the provided coordinates.
Used when all three components of a vector (3D) are needed.
Example:
```
cpp
v3 position = vec3(10, 20, 30);  // Creates a vector with x=10, y=20, z=30
```

```cpp
vec2(int x, int y)
```
The vec2 function creates a 2D vector but returns it in the v3 structure, with z automatically set to 0.

Function Signature:

```cpp
v3 vec2(int x, int y);
```

Explanation:

Parameters:
x: The x-coordinate of the vector.
y: The y-coordinate of the vector.
Returns a v3 structure with the provided x and y, and z set to 0.
Used when only two components (2D) are needed, but the v3 structure is required for consistency.
Example:

cpp
코드 복사
v3 point2D = vec2(10, 20);  // Creates a vector with x=10, y=20, z=0
