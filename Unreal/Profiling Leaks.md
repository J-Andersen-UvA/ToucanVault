Running profiler
First run the insights tool:
```bat
D:\Documents\UnrealEngine\UE_5.7_preview\Engine\Binaries\Win64\UnrealInsights.exe
```
Then your project using trace:
```bat
"D:\UnrealEngine\UE_5.7\Engine\Binaries\Win64\UnrealEditor.exe" ^
"D:\Documents\UnrealEngine\UE_5_7_preview\UE_5_7_preview.uproject" ^
-trace=default,memory,metadata,assetmetadata ^
-tracehost=127.0.0.1
```

Bookmarks to find later in the profiler:
```cpp
TRACE_BOOKMARK(TEXT("Mocap.BeginRecording"));

// Setup
TRACE_BOOKMARK(TEXT("Mocap.TakeRecorderStarted"));

// Recording
TRACE_BOOKMARK(TEXT("Mocap.StopRequested"));

// Cleanup
TRACE_BOOKMARK(TEXT("Mocap.CleanupFinished"));
```
The trace bookmarks can also be put in cmd:
```cmd
Trace.Bookmark RecordingFinished
```


Collecting garbage every frame can help identify what is not being cleaned up:
```cmd
gc.collectgarbageeveryframe
```
