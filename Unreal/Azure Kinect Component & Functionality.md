#AzureKinect #UnrealEngine #UEPlugin


I wrote the plugins in Unreal Engine 5.5.3, but it should be very easily portable to other versions higher. There is not much to the plugin, it acts as a blueprint wrapper.
# Setup Plugin
1. We download the SDK containing the dll's needed. Apparently we need more dependencies that we weren't notified of for that dll. We ran:
```bash
dumpbin /DEPENDENTS "C:\Path\To\Your\Plugin\Binaries\Win64\UnrealEditor-AzureKinectSimple.dll"
```
And we got a dump with all dependencies that I fed to chatGPT.
2. From that we figured out that we needed to enable the MediaFeaturePack in Windows:
```bash
dism /online /add-capability /capabilityname:Media.MediaFeaturePack~~~~0.0.1.0
```
3. We also need to specify the Environment Path to `AZUREKINECT_SDK` because I will use that in the C++ code to find the dll.

Now we are able to use the Kinect for coding in Unreal, or we can create a plugin out of it:
[[UE Plugin & Live‑Coding Setup]]


# Plugin Functionalities
Currently the created C++ Plugin contains ways to read out the <span class="red">colorTexture</span>, <span class="red">depthTexture</span> and the <span class="red">depthBuffer.</span> To use these in a project, you either read them out in C++ or you use the blueprint nodes created in those scripts (<span class="red">GetColorTexture</span>, <span class="red">GetDepthTexture</span> & <span class="red">GetDepthData</span>).
These nodes are childed to the <span class="blue">AzureKinect Component</span>, an actor needs this component to access this data. Or it needs to get it from another actor.

## Applying the ColorTexture/DepthTexture to a plane
![[SettingColorTextureAzure.png]]
- `AzureCameraReference` is a reference to the actorBP in the scene that holds the <span class="blue">AzureKinect component</span>, you may also use the component itself in the blueprint.
- `dynamicMat` is an inbetween, used to reference the actual material that holds the `Texture Sample Parameter2D` node with the name `CapturedTexture`. This enables us to update that value every frame and see the images from the Azure Kinect.
# Know issues
- Its hella slow when i open the component in the details tab during a run. I think it doesn't like to display the images live like that. Solve for now is to just not open the details tab for the component during a run.
- The depth camera returns an octagon, thats just how it is.
