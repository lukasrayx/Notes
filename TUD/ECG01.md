# Einführung

**Motivation**

- Computerspiele
- Filmindustrie
- Betriebssysteme
- Konstruktion & Planung



Morphing: 影像变形

**The Utah Teapot**

**Radiosity:** <u>辐射着色</u>, 这是一种类似光线跟踪的特效。它通过制定在场景中光线的来源并且根据物体的位置和反射情况来计算从观察者到光源的整个路径上的光影效果。在这条线路上，光线受到不同物体的相互影响，如：反射、吸收、折射等情况都被计算在内。

**Rendering**: 渲染

**voxelization:** 体素化



## EINORDNUNG UND BEGRIFFSBESTIMMUNG

### Graphische Datenverarbeitung (GDV)

“Methods and techniques for converting data to and from graphics displays via computer”

![](https://i.imgur.com/ilryxJp.jpg)





**Computer Graphics:**

- **Modelling:** <u>Modellierung</u>, <u>Transformationen</u> , <u>Kurven</u>
- **Rendering / Image Synthesis** : <u>Rasterisierung</u>, <u>Transformationen</u>, <u>Graphikprogr</u>. <u>Beleuchtung</u>, <u>Raytracing</u>
- **Animation** : <u>Transformationen</u>, <u>Kurven</u>



**Die Programmierung graphischer Anwendung findet typischer Weise in vier Schichten statt**

- Anwendung / Graphische Benutzungsschnittstelle (GUI)
- SceneGraph / GameEngine / Processing / SDL / CGV Framework
- OpenGL, DirectX, Vulkan / OpenCL, DirectCompute, CUDA
- Shader - GLSL , HSL , CG / Kernel



# Mathematische Grundlagen der Modellierung

**Poincaré Vermutung  庞加莱猜想**

“任何一个[单连通](https://baike.baidu.com/item/单连通)的，闭的三维[流形](https://baike.baidu.com/item/流形)一定[同胚](https://baike.baidu.com/item/同胚)于一个三维的球面。”

Wenn sich alle geschlossenen Kurven auf einer zusammenhängenden, kompakten und geschlossenen 3D-Fläche im 4D-Raum stetig zu einem Punkt schrumpfen lassen, kann man die Fläche stetig in eine 3-Kugel im 4D-Raum deformieren.



rasterization 光栅化： 将3d图形显示在屏幕上























