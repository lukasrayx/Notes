

## 1.1 OpenGL

### State machine

OpenGL is by itself a large **<u>state machine</u>**: a <u>collection of variable</u>s that define how OpenGL should currently operate. The <u>state of OpenGL</u> is commonly referred to as the OpenGL <u>**context**</u>. When using OpenGL, we often change its state by <u>setting some options,</u> <u>manipulating some buffers</u> and then <u>render using the current context.</u>

### Objects

An **object** in OpenGL is a collection of options that represents <u>a subset of OpenGL's state.</u> For example, we could have an object that represents the settings of the drawing window; we could then set its size, how many colors it supports and so on. One could visualize an object as a C-like struct:

```c++
struct object_name {
    float  option1;
    int    option2;
    char[] name;
};
```

```c++
// 创建对象
unsigned int objectId = 0;
glGenObject(1, &objectId);
// 绑定对象至上下文
glBindObject(GL_WINDOW_TARGET, objectId);
// 设置当前绑定到 GL_WINDOW_TARGET 的对象的一些选项
glSetObjectOption(GL_WINDOW_TARGET, GL_OPTION_WINDOW_WIDTH, 800);
glSetObjectOption(GL_WINDOW_TARGET, GL_OPTION_WINDOW_HEIGHT, 600);
// 将上下文对象设回默认
glBindObject(GL_WINDOW_TARGET, 0);
```

window object target is defined as GL_WINDOW_TARGET

- We first create an object and store a reference to it as an id (the real object's data is stored behind the scenes).
- Then we bind the object (using its id) to the target location of the context (the location of the example window object target is defined as GL_WINDOW_TARGET). 
- Next we set the window options 
- finally we un-bind the object by setting the current object id of the window target to `0`.

## 1.3 Hello Window

VBO :<u>**顶点缓冲对象**</u>, 显卡高速显存的缓冲区，用来保存顶点的信息。

VAO : **<u>顶点数组对象</u>**,包含一个或者多个VBOs的对象，被设计用来存储被完整渲染对象的相关数据信息，如渲染对象的顶点信息和每一个顶点的颜色信息。

由于每渲染一次物体就要用一个VBO，而每次绑定一次VBO就要设置各个的顶点的属性，启动各个属性，代码十分复杂，复用性很差，因为每个物体的属性个数什么的都不一样（也就是说不是同构的），循环根本解决不了。所以就抽象出一层VAO来解决这个问题，相当于复用代码，使之简介快速。只在一开始将所有的VBO绑定对应的VAO就OK了，之后渲染的时候完全就可以绑定VAO，然后你就循环处理同构的VAO就好了。

- 生成VAO
- 绑定VAO
- 生成VBOs
- 绑定VBO
- 给VBO分配数据
- 启动顶点属性 enable attr. array
- Render 时绑定对应的VAO glBindVertexArray
- 清除绑定 glBindVertexArray(0)

## 1.4 Hello Triangle

OpenGL仅当3D坐标在3个轴（x、y和z）上都为-1.0到1.0的范围(Normalized Device Coordinates)内时才处理它。

- **顶点数组对象**：Vertex Array Object，VAO

  - `glEnableVertexAttribArray`和`glDisableVertexAttribArray`的调用。

  - 通过`glVertexAttribPointer`设置的顶点属性配置。

  - 通过`glVertexAttribPointer`调用与顶点属性关联的顶点缓冲对象。

  - ```c++
    //创建VAO
    unsigned int VAO;
    glGenVertexArrays(1, &VAO);
    ```

  - ```c++
    // ..:: 初始化代码（只运行一次 (除非你的物体频繁改变)） :: ..
    // 1. 绑定VAO
    glBindVertexArray(VAO);
    // 2. 把顶点数组复制到缓冲中供OpenGL使用
    glBindBuffer(GL_ARRAY_BUFFER, VBO);
    glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);
    // 3. 设置顶点属性指针
    glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
    glEnableVertexAttribArray(0);
    
    [...]
    
    // ..:: 绘制代码（渲染循环中） :: ..
    // 4. 绘制物体
    glUseProgram(shaderProgram);
    glBindVertexArray(VAO);
    someOpenGLFunctionThatDrawsOurTriangle();
    ```

  

- **顶点缓冲对象**：Vertex Buffer Object，VBO

  - 会在GPU内存（通常被称为显存）中储存大量顶点。
  - `unsigned int VBO; glGenBuffers(1, &VBO);`
  - `glBindBuffer(GL_ARRAY_BUFFER, VBO);  ` 使用glBindBuffer函数把新创建的缓冲绑定到GL_ARRAY_BUFFER目标上
  - `glBufferData(GL_ARRAY_BUFFER, sizeof(vertices), vertices, GL_STATIC_DRAW);`  glBufferData函数会把之前定义的顶点数据复制到缓冲的内存中
    - 第一个参数是目标缓冲的类型
    - 第二个参数指定传输数据的大小(以字节为单位)
    - 第三个参数是我们希望发送的实际数据。
    - 第四个参数指定了我们希望显卡如何管理给定的数据。
      - GL_STATIC_DRAW ：数据不会或几乎不会改变。
      - GL_DYNAMIC_DRAW：数据会被改变很多。
      - GL_STREAM_DRAW ：数据每次绘制时都会改变。

- **索引缓冲对象**：Element Buffer Object，EBO或Index Buffer Object，IBO

OpenGL着色器是用OpenGL着色器语言(OpenGL Shading Language, GLSL)写成的

**顶点数据(Vertex Data)**: 顶点数据是一系列顶点的集合。一个顶点(Vertex)是一个3D坐标的数据的集合。而顶点数据是用顶点属性(Vertex Attribute)表示`fload vertices[]`, xyz位于-1.0 ~ 1.0 之间

任何一个绘制指令的调用都将把图元(Primitive)传递给OpenGL。这是其中的几个：GL_POINTS、GL_TRIANGLES、GL_LINE_STRIP。

**顶点着色器(Vertex Shader)**，它把一个单独的顶点作为输入。顶点着色器主要的目的是把3D坐标转为另一种3D坐标（后面会解释），同时顶点着色器允许我们对顶点属性进行一些基本处理。

- 我们**必须**定义<u>至少一个顶点着色器和一个片段着色器</u>（因为GPU中没有默认的顶点/片段着色器）。

- `#version 330 core layout (location = 0) in vec3 aPos;//版本声明 void main() {    gl_Position = vec4(aPos.x, aPos.y, aPos.z, 1.0); }`
- 在GLSL中一个向量有最多4个分量，每个分量值都代表空间中的一个坐标，它们可以通过`vec.x`、`vec.y`、`vec.z`和`vec.w`来获取。注意`vec.w`分量不是用作表达空间中的位置的（我们处理的是3D不是4D），而是用在所谓透视除法(Perspective Division)上。
- 为了设置顶点着色器的输出，我们必须把位置数据赋值给预定义的gl_Position变量，它在幕后是`vec4`类型的。
- `unsigned int vertexShader; vertexShader = glCreateShader(GL_VERTEX_SHADER);`  创建着色对象
- 附加到着色对象并编译：`glShaderSource(vertexShader, 1, &vertexShaderSource, NULL); glCompileShader(vertexShader);`

图元装配阶段的输出会传递给**几何着色器(Geometry Shader)**。几何着色器把图元形式的一系列顶点的集合作为输入，它可以通过产生新顶点构造出新的（或是其它的）图元来生成其他形状。例子中，它生成了另一个三角形。

几何着色器的输出会被传入**光栅化阶段(Rasterization Stage)**，这里它会把图元映射为最终屏幕上相应的像素，生成供片段着色器(Fragment Shader)使用的片段(Fragment)。在片段着色器运行之前会执行裁切(Clipping)。裁切会丢弃超出你的视图以外的所有像素，用来提升执行效率。

**片段着色器** Fragment Shader : 计算像素最后的颜色输出。

- 在计算机图形中颜色被表示为有4个元素的数组：红色、绿色、蓝色和alpha(透明度)分量，缩写为RGBA。每个分量的强度在0.0到1.0之间。

- `#version 330 core out vec4 FragColor;     void main() {    FragColor = vec4(1.0f, 0.5f, 0.2f, 1.0f); } `

- ```c++
  unsigned int fragmentShader;
  fragmentShader = glCreateShader(GL_FRAGMENT_SHADER);
  glShaderSource(fragmentShader, 1, &fragmentShaderSource, NULL);
  glCompileShader(fragmentShader);
  
  //CL_FRAGMENT_SHADER：着色器类型
  ```

**着色器程序** Shader Program Object: 是多个着色器合并之后并最终链接完成的版本。

- ```c++
  //创建程序对象
  unsigned int shaderProgram;
  shaderProgram = glCreateProgram();
  ```

- ```c++
  glAttachShader(shaderProgram, vertexShader);
  glAttachShader(shaderProgram, fragmentShader);
  glLinkProgram(shaderProgram); 
  //把着色器附加到程序上
  //链接shaderProgram
  ```

**绘制三角形**  `glDrawArrays`

```c++
glUseProgram(shaderProgram);
glBindVertexArray(VAO);
glDrawArrays(GL_TRIANGLES, 0, 3);

```

## 1.5 Shaders

vec4(x, y, z, w) : 纯量：w=1, 向量: w=0

VertexShader可以由VAO或者uniform输入数据

vertexShader输出位置， fragmentShader输出颜色



```c++


//这里要把FragColor = "..." 中...改成 ourColor
const char *fragmentShaderSource = "#version 330 core\n"
    "out vec4 FragColor;\n"
    "uniform vec4 ourColor;\n"
    "void main()\n"
    "{\n"
    "   FragColor = ourColor;\n"
    "}\n\0";

glVertexAttribPointer(0, 3, GL_FLOAT, GL_FALSE, 3 * sizeof(float), (void*)0);
//1.从索引0开始取数据，与顶点着色器中layout(location=0)对应。
//2.size
//3.type
//4.是否希望数据被标准化
//5.步长（Stride），指定在连续的顶点属性之间的间隔。3*sizeOF(float) 一次跳三个float的大小
//6.位置数据在缓冲区起始位置的偏移量。

#ifndef: if not define
#def
...
#endif
//防止头文件.h重复被包含


```

**从文件读取：** file->fileBuffer->stringBuffer->string->charArray

把声明都塞进.h文档





课后第二题？？

报错文档无法呼出？？

怎么用shader.vs和shader.fs？？



## 1.6 Textures

## 1.7 Transformations

## 1.8 Coordinate Systems

## 1.9 Camera

## 1.10 Review













# 2. Lighting

# 3. Model Loading

# 4. Advanced OpenGL

# 5.Advanced Lighting

# 6. PBR

# 7. In Practice