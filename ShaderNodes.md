## Custom Shader Support | Hijacking Blender's Shader Nodes ##
> You can use custom attributes and a restricted subset of shader nodes to generate custom Ogre shaders that supports all the 'pass' and 'texture' options of the OgreDotMaterial format.  This is presented to the user as a 'flat-wrapper' around the OgreDotMaterial format, so a good understanding of how shaders work is required - although once a shader is setup anyone could experiment changing its options.


## Hijacking The Shader Nodes Interface: ##
> In an effort to streamline the artist workflow (and keep this code clean and bugfree) a different approach is taken to determine the rendering pass order and texturing pass order.  Instead of using mixer nodes and their connections, rendering order is simply determined by height of a material or texture node relative to other nodes of the same type.  The blending options for a rendering pass are stored as custom attributes at the material or texture level, not in mixer nodes.  (Mixer nodes DO NOT map well to OgreDotMaterial blending options, so they are completely ignored)
> This sort of hijacking leads to a shader that will not render in blender as it will in Ogre, as a workaround for this problem multiple rendering branches can be used within the same node tree.  You may have multiple 'Output' nodes, blender will only use the first one, the Ogre exporter will look for a second 'Output' node and consider only nodes connect to it.  This enables you to reuse the same texture nodes with the mapping options kept intact and connecting them to another branch of nodes that connect to the blender 'Output' node.  Using this double-branching the artist can preview their work in the blender software renderer, although it may not appear excatly the same - at a minimum texture mapping and animations can be previsualized.

Example - Colored Ambient Setup:
  1. check 'use\_nodes' to initialize shader nodes for the given material
  1. add an 'Extended Material'
    * A). optionally add a 'RGB' input, and plug it into the material ambient input.
    * B). optionally add a 'Geometry' input, select the first vertex color channel, and plug the vertex color output into the material ambient input.

## Hijacked Shader Nodes Advantages: ##
  * Faster reordering of passes and texture blending order.
> > (by hijacking the height of a shader node to determine its rendering order)

  * Improved workflow between the 'Shader-Programmer' and blender artist.  The experienced shader-programmer can setup node trees in blender with placeholder textures.  Later the blender artist can use blender library linking to link the shader into their scene, and update the textures.  The integrated OgreDotMaterial documentation can help the artist understand how they might modify the node tree.

  * Users can minimize the number of materials they must manage within blender because some shader options get 'moved-up' to the shader-node-level; and by exploting the nodes this way, we are ineffect instancing a base material and extending it with extra options like the ambient color.  In the example above a single base material can be referened by two separate node-enabled-materials.  The first node-enabled-material could use a RGB input shader node for the ambient color; while the second node-enabled-material could use a Geometry node (selecting the vertexcolor output).


## Texture Nodes ##
All 'Texture Unit' options of OgreDotMaterial are supported by 'Custom Properties' and the following material nodes:

> Add>Input>Texture
> > . texture

> Add>Input>Geometry
> > . vertex color	[the first layer is supported](only.md)
> > . uv layer

> Add>Vector>Mapping
> > . x and y location
> > . x rotation
> > . x and y scaling