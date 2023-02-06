## iOS 커리어 스타터 캠프

<br>

## 💾 프로젝트 관리 앱 소개
>**프로젝트 기간** : 2022-09-05 ~ 2022-09-16<br>
**소개** : 해야할 일을 3단계로 구분하여 업무를 효율적으로 관리할 수 있는 아이패드 앱입니다. <br>
**리뷰어** : [**제이슨**](https://github.com/ehgud0670)

<br>

### ✅ 선택한 기술 스택

| UI | Local DB | Remote DB | Convention | Dependency Manager|
| -------- | -------- | -------- | -------- |-------- |
| `UIKit`     | `Realm`    | `MongoDB` | `SwiftLint` | `CocoaPods` |

<br>

### 🗂 프로젝트 구조
`MVP` + `MVVM`

<br>

## 💡 기술 스택 선정 이유

<details>
<summary>기술 스택 선정 이유 펼쳐보기</summary>

### 1. Local DB : `Realm`

- [x] **하위 버전 호환성에는 문제가 없는가?**

     <img src="https://i.imgur.com/0JZGWVR.png" width = "200" heigt = "250">
     
     - 현재 [Realm 공식 사이트](https://www.mongodb.com/docs/realm/sdk/swift/realm-database/) 기준으로 위의 사진과 같이 iOS에서는 9.0 이상 부터 지원되고 있습니다.
     - [애플](https://support.apple.com/ko-kr/guide/iphone/iph3e504502/12.0/ios/12.0)에서 지원하고 있는 최소 버전은 iOS 12.0이기 때문에 하위 버전 호환성에 문제가 없다고 생각했습니다.

- [x] 안정적으로 운용 가능한가?
    - 2019 년 봄, MongoDB에 인수되었습니다.
    - 현재 가장 최신 버전인 [v10.28.7](https://github.com/realm/realm-swift/releases)이 3일전에 업데이트가 되었습니다.
    - 이 두 가지를 통해 금전적,기술적 부분으로 지속적으로 지원하고 있다고 느껴 안정적인 운용이 가능하다 생각했습니다.

- [x] 미래 지속가능성이 있는가?
    - [공식 사이트](https://investors.mongodb.com/news-and-events/news-releases/default.aspx)에 따르면 금전적으로 계속 투자를 받고 있습니다.
    - 또한 위에서 언급한 것처럼, Realm 기술적으로도 계속 보완 및 개발을 해나가고 있기 때문에 기술에 대한 미래 지속 가능성도 크다 생각합니다.

- [x] 리스크를 최소화 할 수 있는가? 알고있는 리스크는 무엇인가?
    - 제가 생각한 리스크는 멀티 스레드 환경에서 `thread safe` 하지 않을 수 있다는 것입니다.
    - Realm에서는 보다 안전한 멀티 스레드 환경을 제공하기 위해 [세 가지 규칙](https://www.mongodb.com/docs/realm/sdk/swift/crud/threading/#summary)을 제안했습니다.
    - 멀티 스레드 환경에서 작업을 해보지 않았기에, 이 리스크를 겪은 적이 없지만 위 세 가지 규칙만 따르면 리스크를 최소화 할 수 있다고 생각합니다.

- [x] 어떤 의존성 관리도구를 사용하여 관리할 수 있는가?
    - Realm은 현재 `CocoaPods`와 `Carthage`를 지원하고 있어 이를 통해 관리할 수 있습니다.

- [x] 이 앱의 요구기능에 적절한 선택인가?
    - 이번 프로젝트에서 요구한 프로젝트 할일 리스트는 `TODO`, `DOING`, `DONE` 세가지 상태를 갖고 있습니다.
    - 할일의 상태 변화가 많이 일어날 것 같아, 데이터베이스에 잦은 변화가 필요해보였습니다.
    - 이 때문에 속도면에서 `sqlite`나 `coreData`보다 빠르게 대응할 수 있는 `Realm`을 사용하는 것이 적절하다고 생각했습니다.

<br>

### 2. Remote DB : `MongoDB`

- `Realm`과 호환성을 위해 MonoDB의 Atlas를 사용하기로 했습니다.


<br>


### 3. Dependency Manager: `CocoaPods`
- `CocoaPods`를 선택한 이유는 `Realm`이 지원하는 의존성 관리 도구이기 때문입니다. 
- 또한 `Carthage` 보다 `CocoaPods`이 초기 설정이 더 간단하다고 생각하여 최종적으로 `CocoaPods`을 선택하였습니다.

<br>

### 4. 구조: `MVP` + `MVVM`
- 이전의 프로젝트들을 진행하면서 View와 Model 사이의 의존성이 높아 리팩토링과, View에 대한 테스트를 진행하기가 어려웠습니다.
- 이번 프로젝트에서는 View와 Model 사이의 의존성을 낮추고, testable한 코드를 작성해보고 싶어서 `MVVM` 구조를 선택했습니다.
- 또한 제이슨께서 구두로 말씀해주신 것처럼 다른 하나의 뷰는 `MVP`를 적용하여 두 디자인 패턴에 어떤 차이가 있는지 공부해보도록 하겠습니다!
</details>

<br>

## 구현 화면 📱

| 홈 화면 | 할 일 옮기기 |
|:-------:|:-------:|
| <img src="https://user-images.githubusercontent.com/50102522/216857113-039adfe2-570a-472c-9b12-043815a3cf6b.png" width="500" height="450"/>| <img src="https://user-images.githubusercontent.com/50102522/216857422-a81bd6cc-c08d-4309-8ddb-da6f8cb4ff28.png" width="500" height="450"/>| 

| 할 일 생성 화면 | 히스토리 화면 |
|:-------:| :-------:|
| <img src="https://user-images.githubusercontent.com/50102522/216857486-a0fcc3c3-0353-4172-8b81-7251bb81974d.png" width="500" height="450"/>| <img src="https://user-images.githubusercontent.com/50102522/216857500-9eee2ef3-6df2-4bed-86e3-9a25711f927b.png" width="500" height="450"/>|

<br>

## 실행 영상 🎥

<img src="https://user-images.githubusercontent.com/50102522/216858505-885d6772-583a-4e2c-b147-3b991a49e0d3.gif" width="600" height="450"/>

<br>

## 🥸 기능 설명

#### `MongoDB Atlas`와 연동
- 리모트 서버인 `MongoDB Atlas`와 동기화 되는 기능을 구현

- 생성
<img src = "https://i.imgur.com/70G6zOn.gif" width=700>

- 수정
<img src = "https://i.imgur.com/I4I2lhx.gif" width=700>

- 삭제
<img src = "https://i.imgur.com/Ep60n4o.gif" width=700>

<br>

#### NetWork 모니터링 기능 구현
- `NWPathMonitor`를 이용하여 사용자가 현재 네트워크와 연결이 되어 있는지 모니터링 해주는 `NetworkMonitor` 타입 구현
- 네트워크에 연결이 되어 있지 않을 시, `Alert`을 이용해 사용자에게 알려주는 기능 구현

<img src = "https://i.imgur.com/rjRsR5F.png" width=700>

<br>

#### Histroy 기능 구현
- `popoverPresentationController`를 이용하여 popover 형태의 모달을 만들어주는 기능 구현

<img src = "https://i.imgur.com/TiNuGw3.png" width=700>

<br>

## 핵심 경험 💡
- [x] UIKit 
- [x] DatePicker 
- [x] Realm 
- [x] MongoDB  
- [x] Popover 
- [x] CocoaPods 
