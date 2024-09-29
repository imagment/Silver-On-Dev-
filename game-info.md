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
These are the list of functions, classes, keywords etc.
```cpp
//Vector related
Vec2(int x, int y)
Vec3(int x, int y, int z)

//Object related
void createObject(const std::string name, const std::string& shape);

//Placing related
void place(string objectName, int number, Vec3 position);
void placeSpray(const string objectName, int spawns, Vec3 center, int range);
void placeExactSpray(const string objectName, int count, Vec3 startPosition);

//Drawing related
void draw(Vec3 pos, std::string c);
void drawLine(Vec3 start, Vec3 end, std::string c);
void drawRectangle(Vec3 topLeft, int width, int height, string c);
void drawCircle(Vec3 center, int radius, std::string c);
void drawCircleHollow(Vec3 center, int radius, std::string c);
void drawRectangleHollow(Vec3 topLeft, int width, int height, string c);

//Movement
void setObjectPositionX(string name, int number, int x_offset);
void setObjectPositionY(const std::string name, int number, int y_offset);
void setObjectPositionXY(const std::string name, int number, Vec3 pos);
void setObjectPosition(const std::string name, int number, Vec3 pos);

void setObjectPositionRandom(const std::string& name, int number);
void setObjectPositionToSprite(const std::string& name, int number, const std::string& targetName, int targetNumber);

void moveObjectPositionX(string name, int number, int x_offset); 
void moveObjectPositionY(string name, int number, int y_offset);
void moveObjectPositionXY(const std::string name, int number, Vec3 pos);
void moveObjectPosition(const std::string name, int number, Vec3 pos);

void glideObjectPositionRandom(const std::string& name, int number, float speed) ;
void glideObjectPositionX(string name, int number, int x_offset, float speed);
void glideObjectPositionY(string name, int number, int target_y, float speed);
void glideObjectPositionXY(string name, int number, Vec3 target_pos, float speed);
void glideObjectPositionToSprite(const string& name, int number, const string& target, int targetNumber,float speed);
    
//World related
void setWorldBounds(Vec3 world);

//Component related
void applyComponent(const std::string object, int number, const std::string component, ...);
void removeScript(const std::string objectName, const std::string& scriptToRemove);

//Camera related (in class camera)
void setCam(Vec3 pos, Vec3 scale, int depth);
void printCam();
void flipCamera(int X, int Y); 
void setCameraFlip(int X, int Y); 

void SetCameraFlip(int X, int Y);
void pivotCamera(int angle); 
void addPivotCamera(int angle); 
void shakeCamera(float intensity); 
void zoomCamera(Vec3 V); 
void addCameraDepth(int X); 
void setCameraDepth(int X); 
void moveCamera(Vec3 V); 
void startVideo(int FPS);
void endVideo();
//e.g. camera.printCam()
//e.g. Camera c; c.printcam();

```

