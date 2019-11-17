<h1>Dynamic Kelvinlets</h1>

## About

My final MSc project was an investigation into creating procedural elastic animations in triangular meshes in real time. Using the theory outlined in <a href="https://graphics.pixar.com/library/Kelvinlets/paper.pdf">Regularized Kelvinlets: Sculpting Brushes based on Fundamental Solutions of Elasticity</a> and <a href="https://graphics.pixar.com/library/DynaKelvinlets/paper.pdf">Dynamic Kelvinlets: Secondary Motions based on Fundamental Solutions of Elastodynamics</a> by Fernando de Goes, Doug L. James, I implemented a tool that allows users to author and schedule a series of elastic animations and apply them to a mesh in real time.

In short, the theory mimics the evolution of elastic disturbances by treating the mesh as if it were embedded in an infinite, homogeneous, elastic medium. These assumptions yield closed form solutions that propagate radially with time. In essence, we can exactly determine the elastic disturbance experienced at any point within the medium at any point in time. 

Kelvinlets are fundamental solutions to the elastodynamic equations that serve as building blocks to add together for interesting elastic behaviours. They come in four flavours:
* **Impulse**: The elastic response to an impulse applied at a point.
* **Pinch**: The behaviour exhibited by stretching along one principal axis and contracting in another.
* **Scale**: Uniform expansion or contraction along all principal axes.
* **Twist**: Torsion created by rotating points in the material about a common axis.

## Design

Due to the explorative nature of the project, I adopted a iterative development methodology to implement the tool in three principal stages:
* To determine the viability of the project, it was necessary to create a **proof of concept** applying a single Kelvinlet to a mesh using a simple vertex shader. The original papers apply the theory in the 3D animation software *Houdini*, but I wanted to see how this could be achieved in a simple rendering loop written in DirectX 11.

* The next stage was to apply **multiple Kelvinlets** to the same mesh. Different Kelvinlets require different calculations on the same vertex. Either we branch on the application side, selecting different vertex shaders depending on the desired combination of Kelvinlets, or we branch per vertex, within the shader. The latter choice was found to be optimal due to the cost of switching shaders at runtime.

* The last stage in the project was to allow users to author a **timeline of Kelvinlets** and customise their animations at runtime, using a GUI. This proved the most challenging task and required a large refactoring of the code to minimise dependencies between classes.

## Results

For more details and videos of the application in action, please see the [source code](https://github.com/IM56/Dynamic-Kelvinlets/) and the accompanying videos. In the same GitHub project is also a PDF containing a detailed discussion on the implementation and performance.
