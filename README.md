# Advanced Raytracer

This image was rendered using my raytracer, which was written in **C++**:

![final-image](https://github.com/jakedves/raytracing-coursework/assets/75232368/217beff7-61fc-4363-817e-da2755a192ba)

## Image Generation

1. A photon-mapping pass which emits millions of photons to get an idea of the global illumination in the scene
2. A ray tracing pass to determine the colour for each pixel, using the photon maps for global illumination

The photon-mapping pass required reading and understanding the papers and workshops written by Jensen, who invented the technique. 

## Raytracing Features

1. Global Lighting (reflections/refraction)
2. Accelerated Raytracing (Bounding Boxes, multithreading)
3. Quadratic Surfaces (Cones, ellipses, curved surfaces in general)
4. Constructive Solid Geometries to combine surfaces
5. PolyMesh rendering (`.obj` file parser that constructed triangles, see the teapot in the image)
6. Phong material colouring, with photon mapping support
7. Global illumination by querying the photon map

The code cannot be public to preserve the integrity of the coursework, however feel free to reach out and it can be provided.
