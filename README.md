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

## Render Settings

```cpp
#ifndef MY_RAYTRACER_RENDER_SETTINGS_H
#define MY_RAYTRACER_RENDER_SETTINGS_H

#define TEN_MIL 10000000

// Performance settings

#define ACCELERATE true
#define PARALLEL_PHOTON_MAP false
#define PARALLEL_RAYTRACE true
#define NUMBER_OF_THREADS 8
#define KD_TREE_BOUND 1.1f

// Rendering settings

#define HIGH_POLY true
#define SMOOTH true
#define ANTI_ALIASING_SAMPLES 30
#define GLOBAL_LIGHTING_RECURSE_LIMIT 5
#define GAIN_CONTROL false

// Photon mapping

#define PHOTON_MAPPING true
#define NUMBER_OF_PHOTONS TEN_MIL
#define MAX_PHOTON_BOUNCES 5
#define NUMBER_OF_NEARBY_DIFFUSE_POINTS 6000
#define NUMBER_OF_NEARBY_CAUSTIC_POINTS 400
#define APPLY_CONE_FILTER true
#define CONE_FILTER_CONSTANT 1
#define DIFFUSE_WEIGHT 2.5f
#define CAUSTIC_WEIGHT 0.23f

// Importance sampling

// number limit should be ~half of ith iteration
// the ratio determines how many caustics we should expect
// when doing importance sampling
#define CAUSTIC_BONUS_SAMPLES 100
#define CHECK_iTH_ITERATION  20
#define CAUSTIC_NUMBER_LIMIT 12

// Photon rendering

#define RENDER_PHOTON_MAP false
#define PHOTON_RENDER_RADIUS 0.005f
#define ONLY_RENDER_CAUSTICS false
#define ONLY_RENDER_MAP false

// Image settings

#define HEIGHT 1024
#define WIDESCREEN (16.0f / 9.0f)
#define TV (3.0f / 2.0f)
#define SQUARE 1.0f
#define ASPECT_RATIO SQUARE

#endif //MY_RAYTRACER_RENDER_SETTINGS_H
```
