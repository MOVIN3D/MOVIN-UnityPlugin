# MOVIN Unity Plugin

MOVIN 데이터를 Unity에서 바로 받아 확인할 수 있도록 구성한 샘플 프로젝트입니다.

이 저장소에는 두 가지가 함께 포함되어 있습니다.

- Unity 샘플 프로젝트
- 다른 프로젝트에 가져다 쓸 수 있는 `MOVIN-UnityPlugin.unitypackage`

## Environment

- Unity `6000.0.64f1`
- Universal Render Pipeline (URP)
- Input System `1.17.0`

## Included Contents

- `Assets/MOVIN`
  MOVIN 관련 샘플 에셋, 캐릭터, 씬, 스크립트가 포함되어 있습니다.
- `Assets/MOVIN/Scripts/Core/VMCReceiver.cs`
  OSC/UDP 기반 VMC 메시지를 수신하는 리시버입니다.
- `Assets/MOVIN/Scripts/Core/MocapReceiver.cs`
  수신한 본 포즈를 Unity 캐릭터 Transform에 적용하는 컴포넌트입니다.
- `MOVIN-UnityPlugin.unitypackage`
  기존 Unity 프로젝트로 가져오기 위한 패키지입니다.

## Getting Started

### Option 1. Open This Sample Project

1. Unity Hub에서 이 저장소 폴더를 엽니다.
2. Unity Editor 버전 `6000.0.64f1`로 프로젝트를 실행합니다.
3. `Assets/MOVIN/Scenes` 아래 샘플 씬을 엽니다.
4. Play Mode에서 MOVIN 또는 VMC 송신 데이터를 연결해 동작을 확인합니다.

### Option 2. Import The Unity Package

1. Unity에서 대상 프로젝트를 엽니다.
2. `Assets > Import Package > Custom Package...`를 선택합니다.
3. `MOVIN-UnityPlugin.unitypackage`를 선택해 import 합니다.
4. 필요한 프리팹, 스크립트, 샘플 에셋을 프로젝트에 배치합니다.

## How It Works

`VMCReceiver`는 기본적으로 UDP `11235` 포트에서 VMC 메시지를 수신합니다.

지원하는 대표 메시지 예시는 다음과 같습니다.

- `/VMC/Ext/Root/Pos`
- `/VMC/Ext/Bone/Pos`
- `/VMC/Ext/Blend/Val`
- `/VMC/Ext/Blend/Apply`
- `/VMC/Ext/Cam`

`MocapReceiver`는 수신한 본 이름과 Unity 오브젝트의 본 이름을 매칭해 로컬 포지션과 로테이션을 적용합니다.

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

이 저장소는 Unity 프로젝트에 맞춘 `.gitignore`를 사용합니다.

다음 항목은 Git에서 제외됩니다.

- `Library/`
- `Temp/`
- `Logs/`
- `UserSettings/`
- IDE 생성 파일

또한 대용량 `unitypackage` 파일은 Git LFS로 추적되도록 설정되어 있습니다.

## Notes

- 샘플 프로젝트에는 캐릭터와 데모 씬이 포함되어 있습니다.
- 네트워크 환경에 따라 수신 포트와 바인드 주소를 `VMCReceiver`에서 조정할 수 있습니다.
- 본 이름 구조가 다른 아바타를 사용할 경우 `MocapReceiver`의 탐색 기준을 맞춰야 할 수 있습니다.

## License

라이선스 정책이 정해져 있다면 여기에 추가해 주세요.
