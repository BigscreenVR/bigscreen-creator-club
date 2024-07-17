# Bigscreen Environment Setup
This document will go through the process of setting up your Unity scene to work in Bigscreen. If you have not already, extract the _BigscreenTemplate_v1.unitypackage_ file and put it somewhere accessible. **Completing sections 1-5 are required to get your environment accepted!**

Because Bigscreen is cross-platform for both PCVR and Quest, there are some restrictions in place to ensure your environment runs well within Bigscreen for everyone:
- ❌ No Extensive Scripting: Avoid complex scripts. Simple scripts, like rotating objects, are allowed.
- 🔺Triangle Count Max 120k: Total number of triangles should not exceed **120,000**.
- 📂 File Size Limit: Ensure all environment files (meshes, textures, audio, materials, and scenes) altogether don't exceed **70MB**.
- ⚠️ **No Copyrighted Work**: Make sure you have the rights to use all assets in your environment.
- 🛠️ Unity editor version **2020.3.33f1** is required. Using any newer major version of Unity editor can cause integration issues with your environment.
- 💡 No realtime lighting setups.
- 🔎 At this time, using Normal maps or Metallic maps are not recommended. They won't be used when integrating your environment submission and would only contribute to the allotted size limit.
- 🌐 No baked in materials. If your imported meshes have included materials, you must extract them into your unique materials folder. More details in section 4. 

## 1) Unity Project
_If you already have a Unity project created with your environment in the correct editor version, you can skip to section 2._
You should have an app called _Unity Hub_ installed. Download here: https://unity.com/unity-hub

1. Under _Installs_, ensure Unity installation version **2020.3.33f1** is there. If not, go to https://unity.com/releases/editor/archive in your browser and select _2020.X_ then scroll to _2020.3.33_ and click on _Unity Hub_. This will return you back to Unity Hub to install it.

![image](https://github.com/user-attachments/assets/90a3bdab-1df8-4cf1-bea8-89993a05a561)
![image](https://github.com/user-attachments/assets/3011c061-553c-46ec-91db-c93acbda8d64)


2. In the _Projects_ tab, click _New project_. In _All templates_, look for _3D (Built-In Render Pipeline)_. Make sure your selected editor version is **2020.3.33f1**.
3. Select this template and give it a project name, location, and your org. Finally, click _Create project_.

![image](https://github.com/user-attachments/assets/b6f6efb1-6341-483c-8008-a6a574a12004)

> [!TIP]
> We recommend creating a new project for each environment you plan to build. This will help you avoid mistakes and avoid exporting unnecessary assets that will contribute to the asset size limit. 

<br>
<br>
<br>
<br>
<br>
<br>

## 2) Project Preparation
In the created project from _section 1_, you will start in a _SampleScene_. In the _Project_ window, right click the _Scenes_ folder and delete it.
![image](https://github.com/user-attachments/assets/0fd613cb-45f5-46a5-a221-526d6e26b986)


1. In the top bar of Unity, click _Assets_ > _Import Package_ > _Custom Package..._
2. Go to the _BigscreenTemplate_v2.unitypackage_ file you extracted earlier and open it.
3. An import window will appear in Unity. Make sure all the files are ticked then click _Import_.

![image](https://github.com/user-attachments/assets/0fe36cc4-68e3-4870-a5da-b46682cfa2ec)

4. Open the Bigscreen Creator Club window to start a new project: *Window > Bigscreen Creator Club*

![image](https://github.com/user-attachments/assets/3a25858a-6c44-497a-a943-274afea2e856)

6. Click on *Start Project!* and with the popup that opened, enter your environment name then your Bigscreen username and click *Create Project*.

![image](https://github.com/user-attachments/assets/9666dc83-b916-4cce-8239-af7f8277c563)

7. A new scene with the template setup and the folder setup will be created instantly. The folders created **should contain your environment's assets** to help organize your project and speed up the integration process. You should use the created scene for your environment submission.

![image](https://github.com/user-attachments/assets/4ce7381a-6c1d-461c-8747-47ed548a17e7)

![image](https://github.com/user-attachments/assets/0fea1c0c-9c5e-44e8-80ed-7251f617e600)


<br>
<br>
<br>
<br>
<br>
<br>

## 3) Integrating with the Template
The template has three root objects:
- **_Areas_** -- this contains the seats, collisions, and screen placeholders for Bigscreen to use.
- **_Environment_** -- this should house your environment's mesh GameObjects.
- **_Lighting_** -- this will contain lighting objects for your environment including screen emissives. More on this in the _Lightbaking_ section.

> [!TIP]
> In _TemplateAssets_ > _Prefabs_ > _Environments_, there is a _ScaleReferenceFigure_ asset that you can drag into your scene for referencing the scale of your environment and seating with a Bigscreen avatar. Note: This is not an asset to export with your environment.
> 
> ![image](https://github.com/user-attachments/assets/7d3b21ce-fe4f-4c0c-886c-399dd58b750c)

> [!CAUTION]
> Some objects in the template will have missing script components. **Do not remove these components as they hold important references and doing so will cause integration problems with your submission which will end up not being accepted.**

> [!IMPORTANT]
> All objects in your environment must be contained within the _SceneRoot_.

Let's explain what the objects in the template are for. **Items with (*) are required setup for accepting environment submission.**

### Seats*
There are two seat prefabs for use in Bigscreen:
- **_Seat_** -- these are primarily used for the main viewing seats you want users at. The _bigscreen_ placeholder illustrates the direction the user will orient when teleporting to that seat and the default position a floating monitor will end up when resetting its position.
- **_SeatTransitional_** -- these are the floor panels that are used for moving around the environment. They are typically used in flat open spaces with less suitable viewing spots. The _bigscreen_ placeholder illustrates the default position a floating monitor will end up when resetting its position.

> [!WARNING]
> Do not modify the seat prefabs nor unpack them as it can cause integration problems and your submission will end up not being accepted. They are only meant for moving and rotating around in your environment. You can duplicate or remove the seat objects as you please.

> [!WARNING]
> 15 or more starting seats are required to work with a full room in Bigscreen. It is recommended to keep your max seat count **below 800** with the max _SeatTransitional_ objects being **600** and _Seat_ objects being **200**.

> [!WARNING]
> There should not be any seats that are set inactive. If you don't need a seat object, you must delete it.

> [!TIP]
> We recommend using Unity's snap settings for moving seats around in an even fashion. You can set the snap increment by going to _Edit_ > _Grid and Snap Settings..._ > _Increment Snap_. **You hold _CTRL_ while moving an object to start snapping it in increments.**
>  - **For _SeatTransitional_ objects, they use an increment of _0.8_ for forming a grid.**
>  - **_Seat_ objects can be any spacing you want but it is recommended to have equal spacing when possible.**
> 
> ![image](https://github.com/user-attachments/assets/4661d82b-8ef6-4bd4-9e41-6d0432b8fadf)


The order that users spawn into their seats is sorted based on the upper-most seat in the hierarchy within the _Seats_ object. The first seat at the very top will be the default seat the host spawns at. The seat object below it will be the seat the first user that joins the host's room spawns at then so on and so forth. It is ideal to give the default seats the best possible viewing spot in your environment.
![image](https://github.com/user-attachments/assets/8fa36ec2-e676-44b3-b501-e94061d85e53)


### Screens*
Provided are two screen objects under _Areas_:
- **_ScreenPlaceholder_** -- this is where the primary screen will appear in your environment. It is where the host's desktop and any other screen-related content will be positioned at. You can adjust the position and rotation of this as you please. **There should only be one _ScreenPlaceholder_ in your environment.**
- **_MirroredScreenContainer_** (optional) -- this has the mirrored screen which as the name suggests will mirror what the room host's primary screen is showing. This is optional and if you don't plan to use mirrored screens, it is recommended to delete it from the scene. You can adjust the size of the mirrored screen by changing the size of the inner _MirroredScreen_ object inside the container. Do not change the rotation or position of this object. Only do that on the _MirroredScreenContainer_ itself. You can duplicate the _MirroredScreenContainer_ to add more screens but at this time, we require that you only have 30 mirrored screens or less.

> [!CAUTION]
> The aspect ratio of the _ScreenPlaceholder_ and _MirroredScreen_ must stay as **16:9**. Changing it outside of 16:9 will cause stretching issues of screen content in Bigscreen. You should scale the screens appropriately by enabling the _Scale Tool_ in Unity then dragging the center white cube of the scale tool to change the size of the screen.
> 
> ![image](https://github.com/user-attachments/assets/1c88582e-9379-4a23-a605-3e4152e728d0)

> [!CAUTION]
> When rotating the _ScreenPlaceholder_ object in your environment, you must increment its rotation by 90 degrees starting from 0 on the y-axis. **0, 90, 180, 270, 360** (and so on) are valid rotations. Rotating it otherwise will cause screen lighting to show improperly in your environment. If you do not plan to have screen lighting in your environment, you can rotate as you please.
> 
> ![image](https://github.com/user-attachments/assets/70f4681e-b991-427d-8982-8f043ddd58af)
> ![image](https://github.com/user-attachments/assets/11f28951-8bb1-4029-9294-c0ca6cd0654f)


### Colliders*
It's important to get your environment's collision setup. Otherwise toys will fall through geometry and will not make a good user experience. This is a required step to get your environment submission accepted.
Under _Colliders_, there are four _BoxCollider_ GameObjects representing the collision of the environment. You should add or remove any collider objects and adjust them to suit your environment's needs.
You can resize the _BoxCollider_ objects by using the bounding volume editor.
![image](https://github.com/user-attachments/assets/dc42c629-dbed-4a4c-a37e-56c319ece5ab)


Optionally, you can attach _BoxCollider_ components to your mesh GameObjects and adjust the bounding size there. With that setup, however, you must make sure the Layer assigned to your mesh GameObjects are on _Ignore Raycast_.

> [!NOTE]
> Mesh Colliders are permitted as long as they are used sparingly and are very low poly (under 1,000 triangles). For example, using Mesh Colliders for flat flooring, flat walls, dectorative objects, or duplicated theater seats are not permitted use cases.

> [!WARNING]
> You should aim to have your collision flush with the environment's geometry. Having noticeable collision offset from the ground or floor as an example would not make an acceptable environment submission.

> [!WARNING]
> Avoid having missing collision in areas that users can reach. This can be either from throwing toys or teleporting to areas via seats.

> [!TIP]
> You can check your collision by going to _Window_ > _Analysis_ > _Physics Debugger_ then enable _Gizmos_ and _Collision Geometry_ in the scene view. This will show highlights of your environment's geometry.

### Camera Tool Angles
Under _Cameras_ there are three _CameraAnchor_ objects. These are used by the app's Camera tool's _2, 3, and 4_ angles. The arrows indicate where the camera will position and orient in your environment. You can move and rotate the camera anchors as you please. Avoid changing the inner _Indicator_ object though.
![image](https://github.com/user-attachments/assets/8b19509b-321d-41e0-a107-63c5cee68f21)


### MonitorOcclusionDetector
The bounding box collider of this object is used to tell when a user's floating monitor is outside the environment when switching environments. If a monitor is outside the bounds when entering the environment, the monitor resets to its default position in front of the user. It is recommended to set this BoxCollider boundary size to roughly fit your environment's geometry and just below your primary flooring.
![image](https://github.com/user-attachments/assets/9a30413b-1115-4098-94bf-549dbe601612)


Let's start integrating with the template. In this example, we will walk through making a simple environment with a giant donut and a big screen in front.
1. If not already unpacked, we first right click _SceneRoot_ in the _Hierarchy_ window then click _Prefab_ > _Unpack_.
> [!CAUTION]
> Avoid using _Prefab_ > _Unpack Completely_. Doing this will remove object references that are required for integrating your submission into Bigscreen.

2. We then remove the template's floor and table objects under _Environment_.
3. Next, let's add the donut mesh. We'll take a .fbx donut mesh for this example and copy it into _Models_ > _LargeDonut_Q_Q_ through File Explorer.
4. We will click the _Donut_ mesh and drag it into the _Environment_ object in the _Hierarchy_.

![image](https://github.com/user-attachments/assets/7b14c3d3-34fd-4e77-8926-ae318c73068d)


5. The mesh will need its size and position adjusted.

![image](https://github.com/user-attachments/assets/b90b6bac-7ebc-4847-9c38-468fe5beafcb)


6. Next, we add the materials and give it some color. The materials created will go in _Materials_ > _LargeDonut_Q_Q_

![image](https://github.com/user-attachments/assets/c5274f32-be50-4c62-84e2-19b375fec4c0)


7. Let's adjust the seating. We will keep the transitional seats and setup the diamond seats to be in two rows. The host entering this environment will appear at the selected seat which is the highest in the hierarchy.

![image](https://github.com/user-attachments/assets/f4aec30b-5130-43da-89db-93c6c3aa3479)


8. Next are screens. Let's resize the _ScreenPlaceholder_ to an appropriate size and delete the _MirroredScreenContainer_ as it is not needed for the environment.

![image](https://github.com/user-attachments/assets/edb3f776-7a61-4cd3-bc12-2797d8fd2c98)


9. We will fit the MonitorOcclusionDetector to the environment's spec.

![image](https://github.com/user-attachments/assets/6b85a69d-fdbe-4d87-afb9-b9edf65f2bce)


10. The CameraAnchors need to be adjusted. We will set them in three different angles pointing to where users sit.

![image](https://github.com/user-attachments/assets/b21d2805-7249-4007-83d2-d421bb6d05f0)


11. Finally, colliders are setup. To help aid collision setup, let's enable collider visuals in the scene by going to _Window_ > _Analysis_ > _Physics Debugger_ then enable _Gizmos_ and _Collision Geometry_ in the scene view.
12. Because of the unique shape, we start with a collision segment using the provided _Collider_ objects in the template then duplicate and rotate the segments around the torus shape.

![image](https://github.com/user-attachments/assets/f666f732-6228-4404-ab11-d6eddcf9ab81)

![image](https://github.com/user-attachments/assets/a1189dde-7b20-448b-9acf-37929ff4f6cf)


🎉The scene setup is now done! Next we will look at lightbaking in the next section to get screen lights to work in the environment.

<br>
<br>
<br>
<br>
<br>
<br>

## 4) Materials & Lightbaking
Bigscreen uses lightbaking to emit screen lighting while being performant on PC and Quest. There are two kinds:
- **_lights up_** -- This is what your environment is intended to appear as when no content is showing on-screen. Think of it like a theater's lights turning on once the movie is over.
- **_screen lit_** -- Bigscreen's dynamic lighting engine uses this lightmap to cast the screen's colors onto the environment. This is required for screen lighting to work in your environment.

Both are used when dimming the lights in your environment. When no content is on-screen, the app will fade to your _lights up_ lightmap.

> [!IMPORTANT]
> It is important to assign your meshes with a simple material that's either assigned its texture asset or opaque with color. We recommend using the _Standard_ shader for your materials. When importing your environment into Bigscreen, we will assign the right shaders to the materials so screen lighting can work. **We do not accept having any realtime lighting setups nor complex shaders.** If there is a use case for a unique material or simple shader for object(s) in your environment, let us know about it in your submission ticket.
> 
> **At this time, we require that you use only *Albedo* (RGB) base texture maps on your materials. Support for Metallic and Normal maps with user environments might come in the future but to help keep the size of your assets at a minimum, it is best to have those texture assets absent.**

> [!IMPORTANT]
> Any mesh objects you import into your project must not have baked in materials. When integrating your submission, various shaders are assigned to materials to make the environment work in the app. In situations you import a mesh with included materials, you should extract the material(s) and put it under your unique *UserEnvironments* materials folder created in section 2. Right click the materials inside your model and click *Extract From Prefab* then in the file explorer window, navigate to your project's material folder and select it. *You may need to reassign the extracted materials to your objects.*
> 
> ![image](https://github.com/user-attachments/assets/196f00b9-ad0e-44c9-9e4d-fb38f97d9eb2)
> 
> ![image](https://github.com/user-attachments/assets/89b1491f-a75a-4a02-931f-f6490388c04f)

> [!TIP]
> The Bigscreen Creator Club tool can detect if any meshes in your scene still contain bundled materials. Use the "..." button to examine the materials that need to be extracted.
> 
> ![image](https://github.com/user-attachments/assets/241c6cf7-d961-46b6-a632-5641232fd18b)
>
> ![image](https://github.com/user-attachments/assets/a46aa463-03af-47f7-820b-721ecc740068)

> [!IMPORTANT]
> You must ensure that all of your mesh objects you intend to lightbake with your environment have non-overlapping UV maps or lightmap UVs generated in the model import settings. If you lightbake otherwise, you end up with artifacts and screen lighting will not work appropriate.

> [!IMPORTANT]
> At a minimum, we require that you at least have a _lights up_ lightmap included with your environment. Only exception is if your scene already has suitable lightmaps attached to the mesh GameObjects.

> [!NOTE]
> There are scenarios where a screen lit lightbake of your environment is not needed. Any environments you intend to be fairly lit at all times will not need _screen lit_ lightmap(s) but only the _lights up_ lightmap(s). Screen lighting will not be active in this scenario. **If your environment is intended to be screen lit, you must run the _screen lit_ lightbake first then do _lights up_.**

### Lightbaking Setup
For this guide, we will use the native Unity lightbaking system but any other baking asset you use would work granted that it does not produce separate direction lightmaps. Additionally, we will use the same environment that we have setup in _section 3_.

1. We first need to set all of the environment's mesh GameObjects to _Static_ for lightbakes to use their surfaces.

![image](https://github.com/user-attachments/assets/704add82-189b-4a25-91fa-95ebbb10a3fc)


2. Now we make the _Lighting_ object under _SceneRoot_ active. This contains the screen emissive objects that will emit the lighting for the _screen lit_ lightmap(s).

![image](https://github.com/user-attachments/assets/beae126b-91b5-44c9-8155-4b2ffd41b073)


3. Since we are not using any mirrored screens in this environment, we will remove the screen emissive included in the template that was representing the _MirroredScreenContainer_ object. Optionally, you can duplicate the _ScreenEmissive_ and resize/position it to fit over any mirrored screens your environment contains.

4. We will position then resize the _ScreenEmissive_ to represent the _ScreenPlaceholder_ object in our environment. This is for the _screen lit_ lightmap.

![image](https://github.com/user-attachments/assets/dbb71944-a0ed-4653-b99a-e0b662cd9fc8)


5. The environment needs some lighting for the _lights up_ lightmap. To do this, we add a _Directional Light_ to the scene under _Lighting_ then adjust the position and color. You can use any of the Unity lighting effects in your environment for lightbaking the _lights up_ lightmap. All Unity lighting objects need to have their _Mode_ set to _Baked_. Depending on your scene, you may need to adjust any light object's _Intensity_ to get the desired lightbake output if you find the default value is too dim. Keep in mind if you use a third party lightbake solution, it may have its own objects for emitting light onto a scene.

![image](https://github.com/user-attachments/assets/c5324152-ecb4-43a8-b0fe-794335801a50)

![image](https://github.com/user-attachments/assets/28d3d701-c6b7-4310-9911-6ca05c4b0126)

_It is recommended to enable shadows on your light objects to make your lightbake more realistic. Use *Hard Shadows* or *Soft Shadows* depending on your preference._

![image](https://github.com/user-attachments/assets/7c478612-ff5d-41d5-9cd2-96e2459002b9)


6. With the _lights up_ and _screen lit_ setup done, we hide the _Areas_ object under _SceneRoot_ as we do not want its objects influencing the lighting in the environment.

7. First we start with the _screen lit_ lightbake. We need to set the lights that were setup in _step 5_ as inactive and leave only _ScreenEmissive_ objects active.

![image](https://github.com/user-attachments/assets/80a97c41-dc78-434b-a4f6-a21437578972)


8. Now open the _Lighting_ window by going to _Window_ > _Rendering_ > _Lighting_.

![image](https://github.com/user-attachments/assets/7014ef6c-1479-47ba-9619-67a4fe295992)


9. With the _Scene_ tab active, click on _New Lighting Settings_. This will save a lighting asset to the current folder the _Project_ window has selected. It is recommended to select your lightbake folder under _Lightbakes_ in the _Project_ window so that the file ends up there.

![image](https://github.com/user-attachments/assets/d5591500-0916-4cc5-9185-d35dd6b969a4)

![image](https://github.com/user-attachments/assets/0387fa9c-ebe8-4bf2-9332-41824b4bf322)


10. For _screen lit_, we will need to bake with lighting mode set to _Shadowmask_ and Global Illumination enabled. Additionally, we need to set _Directional Mode_ to _Non-Directional_ so the appropriate lightmap files are produced.

![image](https://github.com/user-attachments/assets/eaa16b58-4155-4d71-84f7-4714a6a1af03)

![image](https://github.com/user-attachments/assets/efb36d54-709e-48c9-8e9b-b1ddde5130d3)


11. We will keep the other settings as default but you may have to tune some numeric values under _Lightmapper_ to suit your environment's needs. You can view more info on these settings here: https://docs.unity3d.com/Manual/progressive-lightmapper.html

12. Now we click _Generate Lighting_ and wait for the process to finish. You can see the progress in the lower right hand corner of the Unity window.

> [!TIP]
> If you find the size of your lightmap files are too large, try lowering the resolution of _Max Lightmap Size_ or the texels value of _Lightmap Resolution_.

13. This is our result for the _screen lit_ lightmap. It seems a little too dim, so let's adjust the _ScreenEmissive_ intensity to emit more light. You may have to adjust this too depending on your environment and lightbake output.

![image](https://github.com/user-attachments/assets/b375d25e-7a76-4dab-a83e-315a6fee62ea)


14. We will select the _ScreenEmissive_ object then scroll down to its material at the bottom of the _Inspector_ window.

![image](https://github.com/user-attachments/assets/a0fb1c95-4a21-4280-9fc4-ab4c8b5f7f2d)


15. From here we select the _HDR_ button under _Emission_ to change the _Intensity_. We will assign its _Intensity_ to 1.25. **For screen lighting to work appropriate in Bigsreen, the color of the _ScreenEmissive_ must stay white.**

![image](https://github.com/user-attachments/assets/0d7b59d0-f9e6-4be7-a002-eeac9d938fcd)


16. Now we open the _Lighting_ window again and rebake as we did in _step 12_. The _screen lit_ bake now looks better. It's best to not make your _screen lit_ lighting too bright that there is little falloff as it can produce unrealistic screen lighting in your environment.

![image](https://github.com/user-attachments/assets/099d58b3-57ba-4c44-ba85-9e3cdb663d9d)


17. With the _screen lit_ lightbake finished, we need to take the produced lightmap files and copy them over to _Lightbakes_ > _ScreenLitVariants_ > _LargeDonut_Q_Q_. You can find the lightmap file location by clicking on a mesh GameObject in your environment, then selecting the _Baked Lightmap_ image in _Inspector_.

![image](https://github.com/user-attachments/assets/7442da17-2ed7-45dd-af4e-ebc188f6a89d)


18. Right click the lightmap file and _Show in Explorer_.
19. The lightbake produced two lightmap files. We will highlight those including its _.meta_ files then copy them.

![image](https://github.com/user-attachments/assets/1777b2dd-57d0-410b-b243-ebb89c0be198)


20. Next we paste those files into the location using File Explorer: _Lightbakes_ > _ScreenLitVariants_ > _LargeDonut_Q_Q_. Unity will show them in the Project window.

![image](https://github.com/user-attachments/assets/3e8c981c-7cfc-4bca-bb03-1d1c13b467b3)

21. Now we move on to lightbaking the _lights up_ lightmap. This is a similar process to _screen lit_.
22. In the _Hierarchy_ window in Unity, set the _ScreenEmissive_ objects to inactive and set all of your lighting objects active.

![image](https://github.com/user-attachments/assets/a33cf5a5-baf9-42d7-a8a1-bb64756d1e14)


23. Now open the _Lighting_ window in Unity and set _Lighting Mode_ to _Baked Indirect_

![image](https://github.com/user-attachments/assets/5c06a614-0048-4704-b65a-43704d731186)


24. Click _Generate Lighting_. After it finishes, we now have our _lights up_ lightmaps.

![image](https://github.com/user-attachments/assets/02cbfdc3-6c2e-4b5f-8b62-292f56fd5b4d)


25. We will need to find the lightmap file again. You can find the lightmap file location by clicking on a mesh GameObject in your environment, then selecting the _Baked Lightmap_ image in _Inspector_.

![image](https://github.com/user-attachments/assets/561900e7-0c0e-4c8d-94da-80550171a56f)


26. This time we will not copy the files but instead move them into _Lightbakes_ > _LargeDonut_Q_Q_.

![image](https://github.com/user-attachments/assets/3ff66e0b-5df8-44e8-b933-0e46e130ffa9)


🎉Lightbaking is now done! Next we will go over exporting your environment so it can integrate into Bigscreen smoothly.

<br>

### Lightbake Troubleshooting
If you are having trouble with lightbaking some objects or with the whole scene, try looking at these common areas:

- Make sure every mesh object in your scene has *Static* enabled in the *Inspector* window.
- All of your light sources should have their *Mode* set to *Baked*.
- If one or more objects are not being assigned a lightmap, select their mesh model in the *Project* window and in the *Model* import settings, enable *Generate Lightmap UVs* then click *Apply*.
- If the lightbake is not bright enough, try increasing the light source(s) *Intensity*.
- Your mesh models should have unwrapped UVs and no UVs that overlap each other. If your lightbake has line looking artifacts, try fixing up the mesh's UVs in a mesh editing program such as Blender or enabling *Generate Lightmap UVs* in the *Model* import settings.
- If your lightmaps have directional variants included (usually suffixed with "dir" in the file name), set the *Directional Mode* to *Non-Directional* in the *Scene* tab of the *Lighting* window then use ***Clear Baked Data*** before baking again!

> [!TIP]
> When making changes to your lightbake setup, it is recommended to clear the current lightbake data before starting a new lightbake. You can do this by clicking on the down arrow ▼ in the *Generate Lighting* button then click ***Clear Baked Data***.

> [!TIP]
> Any objects in your scene that don't have a lightbake attached will surface up in the Bigscreen Creator Club tool. Look to ensure the object is set as static or generate lightmap UVs. Note that not all objects are required to have a lightbake such as unlit emissives, or anything transparent.
>
> ![image](https://github.com/user-attachments/assets/5126c529-0465-439e-b657-e70b852f120a)
>
> ![image](https://github.com/user-attachments/assets/a2fc66f7-cf69-437a-b802-3ffa2e2221d8)

<br>
<br>
<br>
<br>
<br>
<br>

## 5) Exporting your Environment
When exporting your environment, you need to make sure all of your environment's assets are under _UserEnvironments_ and under the subfolders you created from _section 2_. Failure to do so will cause missing assets to occur when integrating your environment into Bigscreen. You must also export assets that are **only used in your environment** and no extra assets left over from other environment projects or what you no longer require.

1. In the scene _Hierarchy_, we need to set the _Lighting_ object to inactive as it is only meant for lightbaking.
2. Then we make the _Areas_ object active again. Its child objects such as _Seats_ must all be active as well. The _Areas_ object only needs to be inactive during lightbakes.
3. Save your Unity scene by using _CTRL + S_ or other means.
4. In the _Project_ window, select _UserEnvironments_ under _Assets_ and right click it.
5. Click _Export Package..._

![image](https://github.com/user-attachments/assets/8054cdc8-8829-4b27-be49-2ec4bc347980)


6. In the _Exporting package_ window, the _TemplateAssets_ folder should be unticked and all of your assets under _UserEnvironments_ should be ticked. If a folder stays unticked, it means no files are in it. You can proceed.

![image](https://github.com/user-attachments/assets/76d27a18-dccf-461b-83d2-7ddbb6c20298)


7. Click _Export..._ and give the package a file name. _Your environment is now ready for submission!_

![image](https://github.com/user-attachments/assets/48a007fb-353e-465b-be4f-5d157d1aea61)
