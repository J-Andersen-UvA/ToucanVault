```mermaid
flowchart TB

    subgraph Host["Host Application (Unreal)"]

        subgraph HostRuntime["Runtime"]
            H1["Skeleton Representation"]
            H2["Animation Data"]
            H3["Retargeting"]

            H1 --> H2 --> H3
        end

        subgraph HostAuthoring["Context Authoring"]
            H4["Point Placement"]
            H5["Relationship / Constraint Editor"]
            H6["Context Configuration"]

            H4 --> H6
            H5 --> H6
        end

        H7["Debug Visualization"]
    end


    subgraph Context["Context Solver"]

        subgraph ContextInput["Solver Input"]
            C1["Point Definitions"]
            C2["Relationship Definitions"]
            C3["Joint Constraints"]
        end

        subgraph ContextEvaluation["Pose Evaluation"]
            C4["Parameter Vector → Joint Pose"]
            C5["Forward Kinematics"]
            C6["Evaluate Context / Contact Points"]

            C4 --> C5 --> C6
        end

        subgraph ContextLoss["Context Evaluation"]
            C7["Descriptors / Point Relationships"]
            C8["Context Weighting"]
            C9["Loss Functions"]

            C7 --> C8 --> C9
        end

        C1 --> C6
        C2 --> C7
        C3 --> C9
        C6 --> C7
    end


    subgraph Math["Math / Optimizer"]
        M1["Parameter Vector"]
        M2["Numerical Gradients"]
        M3["Adam"]

        M1 --> M2 --> M3 --> M1
    end


    H6 --> ContextInput
    H3 --> C4

    M1 -- "Candidate Parameters" --> C4
    C9 -- "Scalar Loss" --> M2

    C4 -- "Final Pose" --> HostRuntime
    C6 --> H7
```
When the source context point is far from other point, there is no reason to make the target reproduce that exact relationship. As the source point approaches the other point, the relationship gradually activates.
This is called adaptive weighting, and is also a reason why adding context points in space and not only on the mesh is important.

One limitation in the paper’s evaluation is that it measures smoothness using the jerk of joint positions. A bone can twist visibly while its joint position barely changes, so their metric could miss exactly this kind of rotational jitter. They report smooth output, but they do not report a bone-orientation jerk metric or discuss twist ambiguity.

normal or orientation only used by penetration currently.

When only hands, face, shoulder context point i noticed a lot of jitter in neutral pose. I solved it by adding more context points.

Relationships on same bone context points are ignored.
