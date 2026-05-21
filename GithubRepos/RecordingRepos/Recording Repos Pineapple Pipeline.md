Github repos for the Signlab recording process.

--- 
## PineapplePipeline-discovery
[J-Andersen-UvA/pineapplepipeline-discovery](https://github.com/J-Andersen-UvA/pineapplepipeline-discovery)
Keep track of mocap streams, add mocap streams, see if they are healthy, act as middleman for an endpoint like SignCollect. You connect interfaces using the config and examples in the scripts folder.
We use zeroconf to communicate the interfaces with the Pineapple Discovery system.
![[Pasted image 20260521145609.png|400]]

## LLFInterface
[J-Andersen-UvA/LLFInterface](https://github.com/J-Andersen-UvA/LLFInterface)
We don't really use this anymore, but if you want to record with the LLF IPhone you would use this repo.
## blackmagic_control
[rem0g/blackmagic_control: Blackmagic Control Suite - web + API](https://github.com/rem0g/blackmagic_control)
In this repo we communicate the camera's service through the blackmagic_pineapple_service folder. Used by pineapplePipeline-discovery.
## OBSRecorder
[J-Andersen-UvA/OBSRecorder](https://github.com/J-Andersen-UvA/OBSRecorder)
Let OBS be controlled through messages, also promotes itself through zeroconf. Used by pineapplePipeline-discovery.
## ShogunLiveInterface
[J-Andersen-UvA/ShogunLiveInterface](https://github.com/J-Andersen-UvA/ShogunLiveInterface)
Let ShogunLive be controlled through messages, also promotes itself through zeroconf. Used by pineapplePipeline-discovery.

--- 
