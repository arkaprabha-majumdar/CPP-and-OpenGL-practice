# Create Window

We will use GLFW for making the window.

We can also use any of these other libraries:
- GLUT
- SDL
- SFML

It works similar to GFLW setup.

We need to create a context, define window params, and handle user input.

# Installation of Framework and Basic Template

We download GLAD zip file from <a>https://glad.dav1d.de/</a>:
- Put the include folder with the glad and KHR on the main repo
- put the src folder with glad.c on the main repo

In CMakeLists.txt, use following commands:

```add_executable(Application application.cpp src/glad.c)
include_directories(include)
add_subdirectory(glfw-3.4)
target_link_libraries(Application glfw)
target_link_libraries(Application opengl32)
```
Then in application.cpp, we call all three required libraries
```#include <iostream>
#include <glad/glad.h> 
#include <GLFW/glfw3.h>
```

Add a method to resize the frame and objects within
```
void framebuffer_size_callback(GLFWwindow* window, int width, int height)
{
    glViewport(0, 0, width, height);
}  
```

Next Steps :
- Initialize glfw with glfwInit()
- glfwWindowHint() helps to configure options:
    - major,minor version gives the version of OpenGL we want to use (highest now = 4.6)
    - setting profile to core profile
- create glfw window object
    ```
    GLFWwindow* window = glfwCreateWindow(800, 600, "LearnOpenGL", NULL, NULL);
    <!-- if (window == NULL)
    {
        std::cout << "Failed to create GLFW window" << std::endl;
        glfwTerminate();
        return -1;
    } -->
    glfwMakeContextCurrent(window);
    ```

- Then we pass glad initialization command
    ```
    gladLoadGLLoader((GLADloadproc)glfwGetProcAddress)
    ```
- set the rendering window
```
glViewport(0, 0, 800, 600);
```
The window size specified earlier is like the program window, but the rendering area is like a canvas that is shown to us.

- Register the frame size change
```
glfwSetFramebufferSizeCallback(window, framebuffer_size_callback);  
```

- The window keeps closing so to keep it open, we use
```
while(!glfwWindowShouldClose(window))
{
    glfwSwapBuffers(window);
    glfwPollEvents();    
}
```

# Few Interesting Points
- The swapbuffers function actually swaps between two 2D imageplanes called buffers, and help to reduce flickering by keeping the other buffer up for the time while the first buffer is rendering.

