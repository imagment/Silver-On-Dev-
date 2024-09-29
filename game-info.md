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
Vec3::up() // Returns a vector (0, 1, 0) representing the upward direction.
Vec3::down() // Returns a vector (0, -1, 0) representing the downward direction.
Vec3::left() // Returns a vector (-1, 0, 0) representing the left direction.
Vec3::right() // Returns a vector (1, 0, 0) representing the right direction.
Vec3::forward() // Returns a vector (0, 0, 1) representing the forward direction.
Vec3::backward() // Returns a vector (0, 0, -1) representing the backward direction.
Vec3::zero() // Returns a vector (0, 0, 0) representing the origin or no movement.
```

Example:
```cpp
Vec2 v1(3, 4);
Vec3 v2(1, 2, 3);
Vec2 result = v1 + v2 + vec3.up; // result is (4, 7, 3)
```


Function Signature:<br>

```cpp
v3 vec2(int x, int y);
```
<br>
Explanation:<br>
<br>
Parameters:<br>
x: The x-coordinate of the vector.<br>
y: The y-coordinate of the vector.<br>
Returns a v3 structure with the provided x and y, and z set to 0.<br>
Used when only two components (2D) are needed, but the v3 structure is required for consistency.<br>
Example:<br>

### Camera

You can set the camera position by using the following function<br>
```cpp
void setCam(v3 pos, v3 scale, int depth);
```

For example,
``` cpp
void setCam(vec2(3,5), v2(4,8), 6);
```
Sets the camera position to 3,5<br>
Sets the camera scale to 4,8<br>
And sets the camera depth to 6.<br>

And you can print the view of the camera by using the following function.<br>
``` cpp
void photo();
```
<br>
This prints the portion of the world.<br>
If there is a object, it prints the object has the minimum Z position<br>
If there is no object, it prints the NULL replacement character.<br>
If there is no object and it is outside of the World, it prints the out of bounds character.<br>
<br>
And instead of printing the camera, you can get the view of the camera by using the following function.<br>
```
vector<vector<string>> gPhoto()
```
This has the similar functionality with `photo()` but it returns the camera view instead of printing it.<br>
Also, `frame()` function would clear the screen and print the camera.<br>

But if you are trying to render the camera, `photo()` and `frame()` would not be a good option. Instead you could use this function<br>

```
void printCam()
```
`printCam()` function is more efficeint because it uses double buffering and reduces blinking.<br>
also, `void startVideo(int FPS)` function would continueously print the camera in another thread. <br>

and to stop the video, you could use
```cpp
void endVideo() {
  isRunningCam = false; 
}
```
<br>
Also, there are more function that could be useful.<br>
```cpp
void flipCamera(int X, int Y); // 1: no change, -1: change
void SetCameraFlip(int X, int Y); // 1: no flip, -1: flip
void pivotCamera(int angle); // Rotate camera
void addPivotCamera(int angle); // Add rotation to camera
void moveCamera(v3 V); // Move camera by vector
void zoomCamera(v3 V); // Zoom camera by vector
void addCameraDepth(int X); // Increase camera depth
void setCameraDepth(int X); // Set camera depth
void shakeCamera(float intensity); // Shake camera
```

### What is Cell size?
if you see the top of this header file, you can see a variable called 'cell size'<br>
```cpp
int cellSize = 2;
```
Cell Size represents the average size (in bytes) of each cell in the game’s grid or map system. It determines how much bytes is allocated for each cell.
But this does not affects the memory usage. However, this affects the output of the world.
<br>
![2](https://github.com/user-attachments/assets/0c298168-9af7-45f2-94d3-5973601fcae8)
<br>Enough cell for each grid (Recommended)<br><br>
![1](https://github.com/user-attachments/assets/ed00f029-303a-426b-92ce-0d620b36ff84)
<br>Insufficient cell size<br><br>
![4](https://github.com/user-attachments/assets/71cfac01-c7a1-4bd2-b93b-15d4ab143d0a)
<br>Increased cell size larger than recommended<br><br><br>




