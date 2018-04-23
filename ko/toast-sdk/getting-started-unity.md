## TOAST > TOAST SDK 사용 가이드 > 시작하기 > Unity

## 지원 환경

* Unity 5.3.4 이상
* Android 4.0.3 이상
* iOS 8.0 이상

## TOAST SDK의 구성

Unity 용 TOAST SDK의 구성은 다음과 같습니다.

* [TOAST Logger](./log-collector-unity) SDK
* [TOAST Crash Reporter](./crash-reporter-unity) SDK

TOAST SDK가 제공하는 서비스 중 원하는 기능을 선택하여 적용할 수 있습니다.

| Unity package | Service |
| --- | --- |
| TOAST-Logger-UnityPlugin.unitypackage | TOAST Logger |
| TOAST-Crash-UnityPlugin.unitypackage | TOAST Crash Reporter |
| TOAST-Sample-UnityPlugin.unitypackage | Sample |

> TOAST-Crash-UnityPlugin 는 Logger에 의존하며, Logger 코드가 함께 포함되어 있습니다.

### Unity package 구조

Unity 용 TOAST SDK는 다음과 같은 폴더 구조로 되어 있습니다.

| Directory | Description | Unity package |
|---|---|---|
| Toast | TOAST SDK의 루트 폴더 | All |
| Toast/Common | TOAST SDK의 공통 모듈 폴더 | All |
| Toast/Logger | TOAST Logger 모듈 폴더 | Logger, Crash, Sample |
| Toast/Crash | TOAST Crash Reporter 모듈 폴더 | Crash, Sample |
| Toast/Sample | SDK 샘플 폴더 | Sample |
| Plugins | Gradle 빌드를 위한 mainTemplate.gradle이 있는 폴더 | All |

## 프로젝트에 Unity package 추가하기

아래의 링크에서 TOAST SDK Unity Package를 내려받습니다.

- [다운로드](../../../Download/#toast-sdk)

### Unity package Import 하기

내려받은 Unity Package 를 더블 클릭하여 프로젝트에 포함합니다.

### Sample 실행하기

Unity 용 TOAST SDK는 별도의 Sample Unity Package 가 있습니다. Sample을 실행하는 방법은 아래와 같습니다.

1. Sample Unity Package 를 더블 클릭하여 프로젝트에 포함합니다.
2. File > Build Settings 에서 Toast/Sample/Sample.unity 를 Scenes In Build 에 추가합니다.
3. Android 혹은 iOS로 빌드합니다.
4. 빌드된 애플리케이션을 실행합니다.

> (주의) Unity SDK는 현재 Android, iOS만을 지원합니다.
> Unity Editor에서는 정상동작하지 않습니다. (지원 예정)

## 설정

### Android

#### Gradle Build 설정하기

* TOAST SDK는 안드로이드 빌드시 Gradle 빌드를 사용합니다.

##### Gradle 빌드 설정 방법
1. File > Build Settings > Android 선택
2. Build System을 Gradle (New) 로 선택
3. Build
    - Signing 관련 에러가 발생할 경우 Development Build 옵션을 On 하고 빌드를 진행하면 됩니다.

### iOS

#### Build Settings 설정하기

* Unity 의 iOS 빌드 설정에는 TOAST SDK가 서버로 로그를 전송하는데 영향을 주는 몇가지 설정들이 있습니다.
* 이 설정들의 효과를 간략히 설명하고 TOAST SDK의 권장 설정에 대해 설명합니다.

| 메뉴 | 목록 | 설정 | 권장 설정 |
| --- | --- | --- | ----- |
| Edit > Project Settings > Player | Debugging and crash reporting | On .Net UnhandledException | Silent Exit |
| Edit > Project Settings > Player | Debugging and crash reporting | Enable CrashReport API | Disabled |
| Edit > Project Settings > Player | Other Settings | Script Call Optimization | Slow and Safe |

##### On .Net UnhandledException

* On .Net UnhandledException를 Crash로 설정할 경우 예외 발생 시, 즉시 앱이 종료됩니다. 
* Silent Exit로 설정해야 Unity Exceptoin을 캡처할 수 있습니다.

##### Enable CrashReport API

* Unity CrashReporter API를 활성화 합니다. Toast Crash SDK를 사용하는 경우 Disabled로 설정합니다.

##### Script Call Optimization

* Runtime C# Crash 로그를 수집하고자 하는 경우 Slow and Safe로 설정해야 합니다.

## 하나의 TOAST SDK로 여러 TOAST 서비스 선택하여 이용합니다.

* [TOAST Logger](./log-collector-unity) 사용 가이드
* [TOAST Crash Reporter](./crash-reporter-unity) 사용 가이드
