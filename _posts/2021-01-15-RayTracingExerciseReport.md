# Lessons I've learned from implementing a Raytracer and translating the reference code from C++ to Rust..

It was a fun project because I got to learn ray tracing and rust together.  

## Things I've learned about ray tracing
There's surprisingly a lot of math which is great since I can see how it translates to code.
Raytracing is (1) generate a ray from each pixel from the camera (2) see what objects the ray intersects (3) compute the color of the intersection (4) continue generating the ray from the intersection and repeat (1) until max depth is reached.
The main shape in this project that used for raytracing were spheres because it has a simple math equations for ray tracing.  
The colors on the spheres are actually according to the surface normals of the points of the spheres.  

There was also a problem where the edges of the sphere's were to0 sharp. Anti-aliasing fixes this by using multiple samples for each pixel
where each sample gets a band of 0 < x < 1 added to the original pixel and averaged over the samples such that the edges blend better.

Diffuse materials like plastic or cement walls uses the intersection point of the sphere to generate another tangent sphere and generate random vectors from inside that other tangent sphere to generate child rays to calculate the correct diffusion color.

Metals (smooth) only reflects so my code is calculating the reflection ray (child ray) and continue the ray until an intersection. There's also the fact that the bigger the sphere, the fuzzier the reflection, so in my code there's a scaler that swings the reflected child ray randomly.

Dielectrics like water, glass, and diamonds actually uses snell's law but with vectors. This material usually has reflection ray and refraction ray childs. There's also a ratio of rays that gets refracted so that not all rays refract on the material. There's the schlick approximation to handle different levels of reflectivity of glass at different angles instead of using tedious accurate formulas.

Positional Camera. Two things current position of camera and the direction to look at for the camera.
Defocus Blur. Since the camera's virtual, it can have extremely accurate details even if the object is really far. So to simulate "Depth of field"(defocus blur), add a focus distance to calculate how blurry an object is from the focus distance.

Render time for the final image took 8 hrs lmao.

## Things I've learned about rust lang
The parameter of the function can be a reference by default which is similar to C++, this makes it seem that the reference is the object itself instead of the pointer.
The rust code checker was really nice because when it checks correctly, I have assurance that the code will work the first time.
The errors from the rust compiler was helpful in fixing the errors but I don't know what they do.
Learning about rust macros were weird because the compiler and handbook was like just put it there.


## Things I did not get to learn
Including modules and then not having to reference everytime from the module. Mainly in main.
I didn't get to stress test the type system of rust.
