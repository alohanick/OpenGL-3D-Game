# OpenGL-3D-Game
shader, model,function,space,stars movement
Shijun Zhang 2021/1/3

Youtube link: https://youtu.be/ynh1QRVjltQ

Game design:
Sorry i change a little game design, before i want to do a serious game that can teach people how to make Chinese food, but later i thought it is very hard to make the kitchen scene,because i can’t draw the model or draw texture. So i change my mind, i want to make a space style, combine the space physical knowledge and food knowledge so i design this game which main content is : Player need to control the space ship and find 4 material: Sauce, Pork, Carrot and broccoli. Then player control the ship return to earth and finish the assignment. If player doesn’t get all of the 4 materials, he won’t win and he need to continue collecting the material until he get 4 materials. And the game hints shows in the console.

Technical and result:

1.Display a 3D polygon mesh 
Use Assimp package to read model .obj file

![image](https://user-images.githubusercontent.com/65901340/103573609-7f103280-4f09-11eb-9d9c-37bad0643c96.png)

Wrote a model class to read and analysis .obj file.

![image](https://user-images.githubusercontent.com/65901340/103573638-86cfd700-4f09-11eb-9e52-8c9bbd66bc3f.png)

Transform the vertex resource to VBO->VAO and get the indices and write in EBO.

![image](https://user-images.githubusercontent.com/65901340/103573541-5ee07380-4f09-11eb-8602-3afad0343509.png)

Function to load image, i write the function in Main.cpp

![image](https://user-images.githubusercontent.com/65901340/103573511-5425de80-4f09-11eb-9747-561a358c7a1e.png)

There are 9 objects in my game so i initialize 9 materials, include specular texture and diffuse texture.Diffuse textures are the Color map of the object itself, Specular texture is a Texture of metal frame.

![image](https://user-images.githubusercontent.com/65901340/103573696-9ea75b00-4f09-11eb-9d43-2deaa36fa2fe.png)

![image](https://user-images.githubusercontent.com/65901340/103573703-a1a24b80-4f09-11eb-9df8-45a4113139bf.png)

At last, i write a draw function to draw the meshes and the function can Automatic identification of diffuse texture and specular texture and transform them to the uniform variable in the shader.

![image](https://user-images.githubusercontent.com/65901340/103573718-abc44a00-4f09-11eb-9c2f-05faa95380c7.png)

![image](https://user-images.githubusercontent.com/65901340/103573726-af57d100-4f09-11eb-8bfa-88e402f374d3.png)

![image](https://user-images.githubusercontent.com/65901340/103573731-b1ba2b00-4f09-11eb-8b92-859ebfd9ec53.png)

![image](https://user-images.githubusercontent.com/65901340/103573734-b383ee80-4f09-11eb-9939-0cb7aa814f58.png)

Interactive manipulation of part of the 3D scene (i.e. transforms) using keyboard/mouse or some other device

In the first person mode, the mouse slides to control the angle of the camera.

![image](https://user-images.githubusercontent.com/65901340/103573741-b7177580-4f09-11eb-840b-133c7f4c9e54.png)

![image](https://user-images.githubusercontent.com/65901340/103573750-ba126600-4f09-11eb-9071-b2956480a47f.png)

![image](https://user-images.githubusercontent.com/65901340/103573756-bbdc2980-4f09-11eb-9e55-f05c55c1917c.png)



The space ship will also adjust the rotation angle according to the angle of the camera.forward direction.

![image](https://user-images.githubusercontent.com/65901340/103573763-bf6fb080-4f09-11eb-853c-5c9d7b0a354b.png)

The Keyboard input:

![image](https://user-images.githubusercontent.com/65901340/103573768-c1d20a80-4f09-11eb-9fbe-6e6e9e173a42.png)

![image](https://user-images.githubusercontent.com/65901340/103573777-c4346480-4f09-11eb-8d0a-40344f06f132.png)

W A S D SPACE Z Control the camera to move up and down, and then the motion matrix of the spacecraft is consistent with the camera, So as to achieve the effect of the spaceship following the camera.
In the Top down view,The keyboard directly controls the motion matrix of the spacecraft model to achieve the effect that the spacecraft does not move and the camera does not move.

![image](https://user-images.githubusercontent.com/65901340/103573784-ca2a4580-4f09-11eb-938c-4a6b8101c105.png)

This is the Camera class and the functions.

hierarchical structure undergoing transformations;
The hierarchical structure is the planets' structure, include planet's rotation and revolution, the game include some Physical formulas to realize the star motivation. The broccoli ,pork and carrot moving around the white star and the white star goes around the sun.
The Sauce moving around the brown star, and the brown moving around the sun.
The moon moving around the earth and the earth also moving around the sun.
All the objects in the game have rotation with different angle velocity, and all the object’s speed of revolution is different. It's astrophysical, objects with small quality has large linear speed. So this game can also teach player some physical knowledge.

![image](https://user-images.githubusercontent.com/65901340/103573822-d8786180-4f09-11eb-8da9-d35e6669d182.png)

Revolution is realized by transform matrix, all the transform matrix is calculated based on their center object. Rotation is realized by rotate matrix.

![image](https://user-images.githubusercontent.com/65901340/103573829-dca47f00-4f09-11eb-970a-8e72271eceb3.png)

![image](https://user-images.githubusercontent.com/65901340/103573831-de6e4280-4f09-11eb-8e25-b1a18764941d.png)

![image](https://user-images.githubusercontent.com/65901340/103573833-e0380600-4f09-11eb-8b2a-8d53dda63ddb.png)

White star and earth move around the sun

![image](https://user-images.githubusercontent.com/65901340/103573840-e332f680-4f09-11eb-94d5-ce90aaed522b.png)

Moon moves around the earth.
Use glfwGetTime() to get system’s time and then the matrix value can change with the time goes.

Lit and shaded; including diffuse and specular objects

![image](https://user-images.githubusercontent.com/65901340/103573859-eaf29b00-4f09-11eb-8bef-85ed04be7e1b.png)

![image](https://user-images.githubusercontent.com/65901340/103573869-ef1eb880-4f09-11eb-9f25-ead14daff2c6.png)

![image](https://user-images.githubusercontent.com/65901340/103573875-f0e87c00-4f09-11eb-8887-4120a70542cd.png)

The Sun is a point light, it is the main light source in the game. 

![image](https://user-images.githubusercontent.com/65901340/103573891-f80f8a00-4f09-11eb-8f10-b7ffda80c846.png)

![image](https://user-images.githubusercontent.com/65901340/103573893-f9d94d80-4f09-11eb-98b8-b2c99a7e6c1c.png)

In shader

![image](https://user-images.githubusercontent.com/65901340/103573897-fba31100-4f09-11eb-8a1f-74f8c9862758.png)
To make the game more interesting , i also added a spot light in front the space ship and it will always in front of the space ship. Now the light show is very beautiful.

![image](https://user-images.githubusercontent.com/65901340/103573903-ffcf2e80-4f09-11eb-8a29-a7abc6a117bd.png)

![image](https://user-images.githubusercontent.com/65901340/103573927-078ed300-4f0a-11eb-9da4-09c25bb839c5.png)

![image](https://user-images.githubusercontent.com/65901340/103573932-09f12d00-4f0a-11eb-8c8c-5f1cffd36acf.png)

![image](https://user-images.githubusercontent.com/65901340/103573941-0bbaf080-4f0a-11eb-910d-5b429168c8b7.png)




Spot light follow the camera.

First person view: The camera is follow the space ship and the ship will rotate withe the mouse move, to ensure the ship is back-toward the camera. 

![image](https://user-images.githubusercontent.com/65901340/103573949-0eb5e100-4f0a-11eb-8296-57979cecf9ae.png)

![image](https://user-images.githubusercontent.com/65901340/103573954-107fa480-4f0a-11eb-9ba2-09ec1a3116f5.png)

![image](https://user-images.githubusercontent.com/65901340/103573964-12e1fe80-4f0a-11eb-9c01-a8d5a79024b4.png)

Top down view: The camera is fixed and the ship won’t rotate with the mouse move, 
WASD SPACE Z still can control the space ship move.

![image](https://user-images.githubusercontent.com/65901340/103573981-17a6b280-4f0a-11eb-86fd-414df3601f15.png)

![image](https://user-images.githubusercontent.com/65901340/103573973-15dcef00-4f0a-11eb-843f-e92b7bc29d3f.png)

![image](https://user-images.githubusercontent.com/65901340/103573983-1aa1a300-4f0a-11eb-8514-aad67d776648.png)


About the shader

Vertex shader:

![image](https://user-images.githubusercontent.com/65901340/103573992-1d9c9380-4f0a-11eb-8e1f-283a0aa9cc39.png)


Fragment shader:

![image](https://user-images.githubusercontent.com/65901340/103573999-1ffeed80-4f0a-11eb-836d-c53ff2604e87.png)

Calculate all the light using normal direction, light direction, and view direction and the diffuse texture, specular texture
 
![image](https://user-images.githubusercontent.com/65901340/103574007-22f9de00-4f0a-11eb-9bbe-76b96d3b71e7.png)

By the way the Reflection model i use is phong model, calculate the reflection light and dot with the view direction.

![image](https://user-images.githubusercontent.com/65901340/103574016-2725fb80-4f0a-11eb-9cec-914d0fe4623a.png)



I new 9 shader objects and different object use different shader.

![image](https://user-images.githubusercontent.com/65901340/103574020-28efbf00-4f0a-11eb-9128-2f7416097529.png)


Give the uniform variable data and use shader to draw.

![image](https://user-images.githubusercontent.com/65901340/103574026-2beaaf80-4f0a-11eb-925e-52d9e30ae427.png)

![image](https://user-images.githubusercontent.com/65901340/103574034-2ee5a000-4f0a-11eb-8644-0079acb1c44b.png)



Game logic judgement: I use position judgement when the space ship’s position is in the range of the pork, sauce, carrot and the vegetable, means player get the food , and if he return to earth now, he will win. How ever if he didn’t get all the food and he return to earth, he won’t win.

![image](https://user-images.githubusercontent.com/65901340/103574046-3311bd80-4f0a-11eb-81f3-7ce47b335219.png)
