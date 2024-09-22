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

### Camera

You can set the camera position by using the following function
```cpp
void setCam(v3 pos, v3 scale, int depth);
```

For example,
``` cpp
void setCam(vec2(3,5), v2(4,8), 6);
```
Sets the camera position to 3,5
Sets the camera scale to 4,8
And sets the camera depth to 6.

And you can print the view of the camera by using the following function.
``` cpp
void photo();
```

This prints the portion of the world.
If there is a object, it prints the object has the minimum Z position
If there is no object, it prints the NULL replacement character.
If there is no object and it is outside of the World, it prints the out of bounds character.

And instead of printing the camera, you can get the view of the camera by using the following function.
```cpp
vector<vector<string>> gPhoto()
```
This has the similar functionality with `photo()` but it returns the camera view instead of printing it.

But if you are trying to render the camera, `photo()` would not be a good option. Instead you could use this function

```
void printCam()
```
`printCam()` function is more efficeint because it uses double buffering and reduces blinking.
also, `void startVideo(int FPS)` function would continueously print the camera in another thread. 


