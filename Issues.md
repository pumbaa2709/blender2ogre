General Warnings:
  * extra vertex groups, can mess up an armature weights (new vgroups must come after armature assignment, not before)
  * quadratic lights falloff not supported (needs pre calc)
  * do not enable subsurf modifier on meshes that have shape or armature animation.
> > (Any modifier that changes the vertex count is bad with shape anim or armature anim)

Current Shader Issues:
  * . You can not create a shader that ends up being more than 16 passes (Ogre limitation)
  * . Shader nodes do not support custom attributes, this limits material attribute overloading.
  * . At this time GLSL in Blender can not compile complex node trees, this will prevent you from seeing the output of the shader in the viewport, not seeing your textures in the viewport is a serious problem.  There are two workarounds:
    * a) disable 'use\_nodes' and assign textures to the material in the normal manner.
> > > [the shader nodes are still exported to Ogre ](.md)
    * b) use a second branch connected to the first 'Output' and preview with software renderer.
