# History of changes #

**2011/02/21**

  * Added RendererActivity.renderContinuously() to allow for pausing and resuming the render loop.

  * SampleProject1 minSdkVersion changed to v1.6 to make it tablet-friendly.


**2011/02/21**

  * Added example of setting up a transparent activity to the sample project, and added method RendererActivity.glSurfaceViewConfig().


**2011/02/20**

  * Light: Fixed important bug where Renderer was (stupidly) setting GL\_SPOT\_CUTOFF to hardcoded value of 45. That, in combination with LightType.DIRECTIONAL and the OpenGL default GL\_SPOT\_EXPONENT value of 0, led to objects seeming to arbitrarily turn off and on, which was the source of much confusion. This should, among other things, fix the non-lit scenes happening on some devices the "Hello Jupiter" and OBJ examples in min3dSampleProject1.

  * Added Light property "spotCutoff" (corresponding to GL\_SPOT\_CUTOFF).

  * Added Light property "spotExponent", corresponding to GL\_SPOT\_EXPONENT.

  * Fixed Object3dContainer.clone(); (thanks Wojciech Musialkiewicz)

  * min3dSampleProject1: Changed linked folder path in Eclipse project properties for min3d source to be relative instead of absolute. Importing project should workon any machine now, without needing to hand-edit the path first (sorry about that).

  * min3dSampleProject1: Fixed layout to Keyframe animation example.


**2010/08/15**

  * Added methods RendererActivity.onUpdateScene() and onUpdateScene() to allow for 3D manipulations from the UI thread.

  * A few minor changes: ManagedLightList.add() and remove() now return booleans (like ArrayList). Apologies for the API change.

**2010/07/14**

  * License changed from GPL v3 to MIT to allow library to be used for commercial purposes.

**2010/06/20**

  * MD2 keyframe animation example added to sample project.

**2010/06/06b**

  * Changed Light.type default to DIRECTIONAL instead of POSITIONAL to match OpenGL default.

  * Fixed or worked around rendering problem which only showed itself in emulator re: lights (ugh).

**2010/06/06**

  * Added light attenuation properties.

  * Added emissive and specular properties to Lights, (These may not useful until emissive and specular properties are added at the Scene level. Not yet tested well.)

  * Added colorMaterial Boolean property to Object3d. I had overlooked this property all this time, leading to the erroneous assumption that use of lighting and per-vertex colors were mutually exclusive (!).

  * Added shadeModel property to Object3d (smooth, flat)

  * Rewrote 'dirty' flag pattern and 'managed' VO classes.

  * Renamed Object3d.colorsEnabled to "vertexColorsEnabled"to avoid confusion with newly added property "colorMaterialEnabled". ("vertexColorsEnabled" determines whether per-vertex color information is used whereas "colorMaterialEnabled" corresponds to GL\_COLOR\_MATERIAL)

**2010/06/03**

  * Added multiple-light support thru ManagedLightList class. Plus property for directional versus positional light. Added multi-light example to sample project. IMPORTANT: Scene no longer supplies default light, so a light should be added manually on scene setup.

**2010/06/01**

  * Minor: Added long-press functionality to sample Project list view to be able to view source.

**2010/05/31**

  * Added MIP mapping option for TextureManager textures. This has necessitated adding an extra argument to TextureManager.addTextureId(). Also added mipmap argument to Parser-related constructors. Added example to sample project.

  * Improved FPS calculation method in Renderer. Added availMem property.

**2010/05/24**

  * **Added animated MD2 parser**, plus example in the sample project

**2010/05/23**

  * Added example to sample project demonstrating how to add 3d to a normal Android layout

**2010/05/23**

  * Added alternate constructors to Object3D and Vertices with three new arguments that determine whether vertex information will be added for texture coordinates, normals, and colors, respectively. It's useful to set these to false, when appropriate, to minimize memory usage and probably increase performance.

  * Added example Activity "ExampleVerticesVariations" to sample project.

  * Renamed "MeshData" class to "Vertices" (sorry about that).

  * In sample project, updated all textures dimensions to 256x256 or 512x512. Amazingly, non-standard dimensions worked fine on N1 until Froyo update.

**2010/05/19**

  * **Added 3DS parser**

  * **Added multiple-objects support to OBJ parser.**

  * Added examples to sample project.

  * Bug fixes in parser package.


**2010/05/16**

  * **Added min3d.parser package, and OBJ importer.**

  * Added ExampleLoadObjFile Activity to sampleProject1

  * Added RenderType "LINES", for line drawing

  * Added properties "lineWidth", "lineSmoothing", and "pointSmoothing" to Object3d.

  * Changed rendering behavior of Rendertype.POINTS to draw using faces list by default, rather than using glDrawArrays.

  * Replaced/added sampleProject1 example "ExampleRenderType.java" accordingly.

  * Added Object3d property "ignoreFaces", which will ignore the faces list and render using the points (vertices) list instead (ie, using glDrawArrays instead of glDrawElements).

  * Added static class "RenderCaps" describing the hardware's OpenGL capabilities relevant to the library.

  * Added tesselation params to min3d.objectPrimitives.Rectangle; need to do same for Box.


**2010/05/14**

  * Added new properties on TextureVo -- offsetU, offsetV, repeatU, and repeatV.

  * Updated Renderer accordingly.

  * Added two examples to sampleProject1 demonstrating.

**2010/05/11**

  * Added multi-texture support, including customizable glTexEnvx() parameters, necessitating change to the API in terms of Object3d setup. See updated sample project for usage details.
    1. Bitmaps must now be added through the new TextureManager before textures can be assigned to Object3d's.
    1. Added TextureVo class, which contains texture-related properties.
    1. Object3d's now contain a textures() list, to which TextureVo's are added.
    1. For now, multiple textures used by an Object3d are limited to using the same UvBufferList (U/V texture coordinates list). To allow separate textures to use separate texture coordinate lists will require some unfortunate structural changes and changes to the API.

  * sampleProject1 has a new example demonstrating the multi-texture feature. Project has been refactored for the above changes.

  * Current featureset seems to work as consistently on Android v1.5 emulator as on Nexus One hardware running Android v2.1.

  * Fixed spelling of frustum and vertices throughout project. Any class names and identifiers using the incorrect spelling of these two words have been changed.

  * VertexInfo class has been renamed MeshData


**2010/05/07**

  * Scene now resets onSurfaceCreate (i.e., not only on startup, but when Activity resumes after losing focus)

  * Misc changes to API, not too major. Other adjustments to plumbing.

  * Committed a fairly complete sample project of framework usage examples to SVN in /trunk/sampleProjects/min3dSampleProject1. Could be fairly useful. Added executable apk file of it to Downloads.

**2010/05/05**

  * First commit.