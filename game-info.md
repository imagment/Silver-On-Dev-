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
Also, `frame()` function would clear the screen and print the camera.

But if you are trying to render the camera, `photo()` and `frame()` would not be a good option. Instead you could use this function

```
void printCam()
```
`printCam()` function is more efficeint because it uses double buffering and reduces blinking.
also, `void startVideo(int FPS)` function would continueously print the camera in another thread. 

and to stop the video, you could use
```cpp
void endVideo() {
  isRunningCam = false; 
}
```

Also, there are more function that could be useful.
```cpp
void flipCamera(int X, int Y); // 1: no change, -1: change
void SetCameraFlip(int X, int Y); // 1: no flip, -1: flip
void pivotCamera(int angle); // Rotate camera
void addPivotCamera(int angle); // Add rotation to camera
void moveCamera(v3 V); // Move camera by vector
void zoomCamera(v3 V); // Zoom camera by vector
void addCameraDepth(int X); // Increase camera depth
void setCameraDepth(int X); // Set camera depth
```

### What is Cell size?
if you see the top of this header file, you can see a variable called 'cell size'
```cpp
int cellSize = 2;
```
Cell Size represents the average size (in bytes) of each cell in the game’s grid or map system. It determines how much bytes is allocated for each cell.
But this does not affects the memory usage. However, this affects the output of the world.

![2](https://github.com/user-attachments/assets/0c298168-9af7-45f2-94d3-5973601fcae8)
Enough cell for each grid (Recommended)
![1](https://github.com/user-attachments/assets/ed00f029-303a-426b-92ce-0d620b36ff84)
Increased cell size larger than recommended
![4](https://github.com/user-attachments/assets/71cfac01-c7a1-4bd2-b93b-15d4ab143d0a)
Insufficient cell size

