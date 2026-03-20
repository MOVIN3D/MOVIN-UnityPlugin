# MOVIN Unity Plugin

This repository contains a sample Unity project for receiving and previewing MOVIN data in Unity.

It includes both:

- A complete Unity sample project
- A reusable `MOVIN-UnityPlugin.unitypackage` for importing into an existing Unity project

## Environment

- Unity `6000.0.64f1`
- Universal Render Pipeline (URP)
- Input System `1.17.0`

## Included Contents

- `Assets/MOVIN`
  Sample assets, characters, scenes, and scripts related to MOVIN
- `Assets/MOVIN/Scripts/Core/VMCReceiver.cs`
  A lightweight OSC/UDP-based VMC receiver for Unity
- `Assets/MOVIN/Scripts/Core/MocapReceiver.cs`
  A component that applies received bone poses to a Unity character transform hierarchy
- `MOVIN-UnityPlugin.unitypackage`
  A Unity package for importing the plugin and related assets into another project

## Getting Started

### Option 1. Open the Sample Project

1. Open this repository folder from Unity Hub.
2. Use Unity Editor version `6000.0.64f1`.
3. Open one of the sample scenes under `Assets/MOVIN/Scenes`.
4. Enter Play Mode and connect your MOVIN or VMC data source.

### Option 2. Import the Unity Package

1. Open your target Unity project.
2. Select `Assets > Import Package > Custom Package...`.
3. Choose `MOVIN-UnityPlugin.unitypackage`.
4. Import the package and place the required assets or scripts into your scene.
5. Make sure the same `.fbx` character model used in MOVIN Studio is also loaded in your Unity project.

## How It Works

`VMCReceiver` listens for VMC messages over UDP, using port `11235` by default.

Supported message examples include:

- `/VMC/Ext/Root/Pos`
- `/VMC/Ext/Bone/Pos`
- `/VMC/Ext/Blend/Val`
- `/VMC/Ext/Blend/Apply`
- `/VMC/Ext/Cam`

`MocapReceiver` maps incoming bone names to Unity transforms and applies the received local position and rotation values.

For best results, MOVIN Studio and the Unity project should use the same `.fbx` character model, or at minimum a character with the exact same bone naming hierarchy.

## Project Structure

```text
Assets/
  MOVIN/
    Character/
    Scenes/
    Scripts/
Packages/
ProjectSettings/
MOVIN-UnityPlugin.unitypackage
```

## Git Notes

This repository uses a Unity-friendly `.gitignore`.

The following generated folders and files are excluded from version control:

- `Library/`
- `Temp/`
- `Logs/`
- `UserSettings/`
- IDE-generated files

The large `unitypackage` file is tracked with Git LFS.

## Notes

- The sample project includes demo characters and scenes.
- You can change the listening port and bind address in `VMCReceiver` if needed.
- MOVIN Studio and Unity should use the same `.fbx` character model whenever possible.
- If the bone names or hierarchy do not match, pose mapping may fail or behave incorrectly.
- If your avatar uses a different bone naming structure, you may need to adjust the search or mapping behavior in `MocapReceiver`.

## License

Add your project license information here if needed.
