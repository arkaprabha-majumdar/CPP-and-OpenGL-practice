# OpenGL

Open GL is not an API, but rather a specification.
Its embedded within our system drivers, and GPUs.

OpenGL is therefore implemented differently by different graphics card manufacturers, and may or may not be open source.

OpenGL till v3.2 was in immediate mode, which was easier to learn, yet inefficient and lacked detailed control on the internal graphics pipeline.
From v3.2 onwards, the core-profile mode was introduced, and immediate mode was deprecated.

OpenGl's modern core-profile mode is efficient and flexible.

OpenGl also supports a variety of extensions that allows functionality provided by the extension for more advanced or efficient graphics.

# State Machine

Open GL is in essence a large state machine, ie, a collection of variables that tell how OpenGL should currently operate.

Current state is called \<context>.
We can change its state by 
- setting options
- manipulating buffers

OpenGL libraries are written in C.

# Objects

An <b>object</b> in openGL is a collection of options:

<code>
struct object_name {

    float option1;
    int option2;
    char[] name;
}
</code>

and we can use the object like:

<code>
struct OpenGL_Context {

    ...
    object_name* object_Window_Target;
    ...
}
</code>

# Usual steps in OpenGL

This little piece of code is a workflow you'll frequently see when working with OpenGL. We first create an object and store a reference to it as an id (the real object's data is stored behind the scenes). Then we bind the object (using its id) to the target location of the context (the location of the example window object target is defined as GL_WINDOW_TARGET). Next we set the window options and finally we un-bind the object by setting the current object id of the window target to 0. The options we set are stored in the object referenced by objectId and restored as soon as we bind the object back to GL_WINDOW_TARGET.

<code>

unsigned int objectId = 0;

glGenObject(1, &objectId);

glBindObject(GL_WINDOW_TARGET, objectId);

glSetObjectOption(GL_WINDOW_TARGET, GL_OPTION_WINDOW_WIDTH,  800);

glSetObjectOption(GL_WINDOW_TARGET, GL_OPTION_WINDOW_HEIGHT, 600);

glBindObject(GL_WINDOW_TARGET, 0);
</code>