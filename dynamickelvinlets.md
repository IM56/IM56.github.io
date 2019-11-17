<h1>Dynamic Kelvinlets</h1>

## About

My final MSc project was an investigation into creating procedural elastic animations in triangular meshes in real time. Using the theory outlined in <a href="https://graphics.pixar.com/library/Kelvinlets/paper.pdf">Regularized Kelvinlets: Sculpting Brushes based on Fundamental Solutions of Elasticity</a> and <a href="https://graphics.pixar.com/library/DynaKelvinlets/paper.pdf">Dynamic Kelvinlets: Secondary Motions based on Fundamental Solutions of Elastodynamics</a> by Fernando de Goes, Doug L. James, I implemented a tool that allows users to author and schedule a series of elastic animations and apply them to a mesh in real time.

In short, the theory mimics the evolution of elastic disturbances by treating the mesh as if it were embedded in an infinite, homogeneous, elastic medium. These assumptions yield closed form solutions that propagate radially with time. In essence, we can exactly determine the elastic disturbance experienced at any point within the medium at any point in time.

## Design

Due to the explorative nature of the project, I adopted a iterative development methodology to implement the tool in three principal stages:
* To determine the viability of the project, it was necessary to create a **proof of concept** using a simple vertex shader.
