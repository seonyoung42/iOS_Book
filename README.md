# iOS_Book
iOS 관련 주제들을 공부하는 repo 입니다

[iOSInterviewquestions](https://github.com/JeaSungLEE/iOSInterviewquestions) 의 자료를 기반으로 하였고, 개인적으로 중요하다고 여기는 주제들을 추가하고 있습니다.

## iOS
<details> 
  <summary> Bounds 와 Frame 을 설명하시오. </summary>
  
  ```
  bounds: 자신을 기준으로 view의 위치와 크기를 표현
  frame: 슈퍼뷰를 기준으로 view의 위치와 크기를 표현
  ```
  
</details>

<details> 
  <summary> 실제 디바이스가 없을 경우 개발 환경에서 할 수 있는 것과 없는 것을 설명하시오. </summary>
  
  ```
  할 수 있는 것 : 애플페이, face id
  할 수 없는 것 : 카메라, push 알림
  ```
  
</details>

<details> 
  <summary> 앱의 콘텐츠나 데이터 자체를 저장/보관하는 특별한 객체를 무엇이라고 하는가? </summary>
  
  ```
  UserDefaults
  : 앱이 실행되는 동안(런타임) Key-Value 형태로 데이터를 저장하는 사용자의 기본 데이터베이스에 대한 인터페이스
  
  - 대용량의 데이터보다 단일 데이터(ex 사용자 기본 설정, 로그인 여부 등)를 저장하는데 더 적합
  - 싱글톤 패턴으로 설계되어 앱 전체에 단 하나의 인스턴스만 존재
  ```
 
</details>

<details> 
  <summary> 앱 화면의 콘텐츠를 표시하는 로직과 관리를 담당하는 객체를 무엇이라고 하는가? </summary>
  
  ```
  UIViewController
  : UIKit 기반 앱의 뷰 계층 구조를 관리하는 객체
  
  - 데이터의 변경에 대한 응답으로 뷰의 업데이트
  - 뷰 크기 조정 및 전체 인터페이스 레이아웃 관리
  - 뷰와의 사용자 상호 작용에 응답
  ```
</details>

<details> 
  <summary> App thinning에 대해서 설명하시오. </summary>
  
  ```
  App thinning
  : 사용자의 기기와 OS버전에 맞춰 필요한 앱 번들을 만들고 전달하는 것
  
  - App store와 OS가 사용자의 기기와 OS버전에 맞게 App의 기능을 제공하고 설치공간을 최소화하여 App 설치 최적화
  - 더 빠른 다운로드와 더 많은 공간을 제공
  - App thinning 방법 
    - Slicing : App store가 앱이 지원하는 기기 및 OS 버전에 따라 다양한 변형(App variant)를 제공하는 것
    - Bitcode : Appstore가 다운로드되기전에 디바이스에 맞게 앱을 최적화 하여 바이너리를 새로 만들어 제공하는 것
    - ODR(= Order-Demand-Resource, 주문형 리소스) : 사용자에게 해당 리소스가 필요할 때 그 리소스를 앱스토어에서 가져오는 것
  ```
</details>

<details> 
  <summary> @main에 대해서 설명하시오. </summary>
  
  <img width="436" alt="스크린샷 2023-06-17 오후 6 06 53" src="https://github.com/seonyoung42/iOSInterviewquestions/assets/77603632/c479ec91-bd4e-4876-816a-a28e26825612">

  ```
  @main
  : 프로그램 실행 시작 시 진입점을 지정하기 위한 Swift 언어의 기능
  
  @main을 선언해줌으로써 UIKit 앱의 진입점은 해당 클래스가 되고 시스템은 UIApplicationDelegate 프로토콜에 구현되어있는 정적 main() 함수를 호출하게 된다
  ```
  
</details>

<details> 
  <summary> 앱이 foreground와 background에 있을 때 어떤 제약사항이 있는지 설명하시오 </summary>

  ```
  Foreground mode
  : 메모리 및 기타 시스템 리소스에 높은 우선순위를 가지며 OS는 이러한 리소스를 사용할 수 있도록 필요에 따라 background 앱을 종료한다.

  Background mode
  : 가능한 적은 메모리공간을 사용해야한다는 제약사항이 이 사용자 이벤트를 받기 어렵고 이미지 객체 참조 등에 대한 메모리도 제한된다.
  
  ```
  
</details>

<details> 
  <summary> 상태 변화에 따라 다른 동작을 처리하기 위한 sceneDelegate 메서드들을 설명하시오. </summary>

  ```swift

  func sceneDidDisconnect(_ scene: UIScene) {
        // Background로 들어간 직후나 세션이 삭제되었을 때 호출
  }
    
  func sceneDidBecomeActive(_ scene: UIScene) {
        // In-Active -> Active 로 변경될 때 호출
  }

  func sceneWillResignActive(_ scene: UIScene) {
        // Active -> In-Active 로 변경될 때 호출
  }

  func sceneWillEnterForeground(_ scene: UIScene) {
        // Background -> Foreground 로 변경될 때 호출
  }

  func sceneDidEnterBackground(_ scene: UIScene) {
        // Foreground -> Background 로 변경될 때 호출
  }
  ```
  
</details>

<details> 
  <summary> App의 생명주기 </summary>

  <img width="355" alt="스크린샷 2023-06-28 오후 9 59 26" src="https://github.com/seonyoung42/iOS_Book/assets/77603632/782b12d6-c456-49a6-8572-cef8c78b08e3">

  ```
  Unattached : 앱이 실행되지 않은 상태
  Foreground : APP이 실행되어 보여지고 있는 상태
    - Active : 앱이 실행중이며 현재 이벤트를 받고 있는 상태
    - Inactive : 앱이 실행중이지만 아무런 이벤트를 받지 않은 상태 (Foreground 상태에서 전화가 오거나, 잠금상태, 런치 스크린에서 InActive 상태가 된다.)
  Background : APP이 보여지고 있지는 않지만 여전히 실행되고 있는 코드가 있는 상태
  Suspened : 실행되는 코드가 없는 상태
  ```
  
</details>

<details> 
  <summary> 앱이 In-Active 상태가 되는 경우를 설명하시오. </summary>

  ```
  1. 전화나 메세지 같은 인터럽트가 발생하는 경우
  2. 알림창이 화면을 덮어 앱이 이벤트를 받을 수 없는 경우
  3. 앱이 Background -> Foreground가 될 때 In-Active를 거쳐 Active가 됨
  4. 앱이 Unattached -> Foreground가 될 때 In-Active를 거쳐 Active가 됨
  ```
  
</details>

<details> 
  <summary> ViewController의 생명주기 </summary>

  ```
  1. loadView : 컨트롤러가 관리하는 뷰를 생성한다. 뷰컨트롤러가 생성되고 순차적으로 완성되었을때 호출된다.

  2. viewDidLoad : 컨트롤러의 뷰가 메모리에 올라간 뒤에 호출된다. 뷰가 생성될때만 호출된다.

  3. viewWillAppear : 화면에 뷰가 표시될때마다 호출된다.

  4. viewWillLayoutSubviews : 뷰컨트롤러에게 그 자식뷰의 레이아웃을 조정하는 것에 대한 것을 알려주기위해 호출된다. frame이 바뀔때마다 호출된다.

  5. viewDidLayoutSubviews : 뷰가 그 자식 뷰의 레이아웃에 영향을 준 것을 뷰컨트롤러에게 알려주기 위해 호출된다. 뷰가 그 자식 View의 레이아웃을 바꾸고난 뒤에 추가적인 변경을 하고 싶을때 사용

  6. viewDidAppear : 뷰가 나타났다는 것을 컨트롤러에게 알리는 역할을 한다. 뷰가 화면에 나타난 직후에 호출된다.

  7. viewWillDisappear : 뷰가 사라지기 직전에 호출된다. 뷰가 삭제 되려고하고있는 것을 ViewController에게 알린다.

  8. viewDidDisappear : 뷰가 사라진 후 호출된다. ViewController에게 View가 제거되었음을 알린다. 
 
  ```
  
</details>

<details> 
  <summary> Higher Order Function이란?  </summary>

  ```
  HOF(= 고차함수) 란 함수를 다루는 함수로 함수를 인자로 전달받거나, 함수 실행의 결과로 함수를 리턴하는 함수이다.

  Swift에서 HOF에는 Map, filter, Reduce 등 이 있다.

  1. Map : 기존 데이터를 변형하여 새로운 컨테이너 생성
  doubledNumbers = numbers.map { $0 * 2 }

  2. Filter : 컨테이너 내부의 값을 거른 새로운 컨테이너 생성
  filteredNumbers = numbers.filter { $0 % 2 == 0 }

  3. Reduce : 컨테이너 내부의 데이터들을 하나로 통합
  sumOfNumbers = numbers.reduce(0) { $0 + $1 }

  ```
  
</details>

<details> 
  <summary> 동기와 비동기 </summary>

  ```
  1. 동기 : 주어진 명령을 차례대로 처리하되 하나의 업무가 완료될 때 까지는 다른 업무로 넘어가지 않는 방식
  2. 비동기 : 주어진 명령을 차례대로 처리하되 시간이 걸리는 업무는 진행 해둔 채 기다리는 동안 다른 업무를 처리하는 방식
  ```
  
</details>

<details> 
  <summary> 동시성 프로그래밍 과 병렬성 프로그래밍 </summary>

  ```
  1. 동시성 프로그래밍 : 시간을 분할하여 스레드들에게 서로 번갈아가며 제공하여 실행되게끔 하는 방식으로 동시에 여러 프로그램을 돌리는 것처럼
  보이는 하는 프로그래밍
  => 동시성 프로그래밍을 구현하기 위해서 비동기 프로그래밍을 활용
  => Apple 에서는 동시성 프로그래밍을 지원하기 위해 GCD 제공

  2. 병렬성 프로그래밍 : 멀티 코어에서 멀티 스레드를 동작시키는 방식으로 실제로 동시에 여러 프로그램을 돌리는 프로그래밍
  ```
  
</details>

<details> 
  <summary> GCD API 동작 방식과 필요성에 대해 설명하시오. </summary>

  ```
  GCD : 애플이 동시성 프로그래밍을 지원하기 위해 만든 기술로 프로그래머가 실행할 작업을 Dispatch Queue에 추가하면 GCD가 작업에 맞는 스레드를 자동으로 생성해서 실행하고 스레드를 제거한다.

  - DispatchQueue는 2개의 타입( Serial / Concurrent )으로 구분되며 둘 모두 FIFO 순서로 처리
  - 앱을 실행하면 시스템이 자동으로 메인스레드 위에서 동작하는 Main 큐(Serial Queue)를 만들어서 작업을 수행하고, 그 외에 추가적으로 여러 개의 Global 큐(Cuncurrent Queue)를 만들어서 큐 관리
  - 각 작업은 동기(sync) 방식과 비동기(async) 방식으로 실행 가능하지만 Main 큐에서는 async 만 사용 가능

  1) Main Queue : 메인스레드에서 작동하는 큐 (UI, 사용자 인터렉션 관련 처리)

    DispatchQueue.main.async {
    // Task
    }

  2) Global Queue : 우선순위(Qos = Quality of Servie) 지정하여 작동하는 큐

    DispatchQueue.global(qos : .background).async {
    // Task
    }

  GCD의 필요성 : GCD를 사용하면 스레드 생성, 유지, 삭제 등을 개발자가 신경쓸 필요 없이 작업(코드)을 큐에 예약하기만 하면 되기 때문에 스레드 관리가 용이해지고 성능이 증가한다.
  ```
</details>

<details> 
  <summary> Async / Await </summary>

  ```
  Async Await 란 비동기를 처리하는 기능으로, completion Handler의 단점을 해결해준다.
  completion Handler를 사용하며 발생하는 코드의 depth와 클로져를 없애며 비동기 코드를 동기처럼 작성할 수 있게 도와준다.

  // 예제
  print("A")
  Task {
    let returnStr: String = try await asyncMethod()
  }
  print("B")

  func asyncMethod() async throws -> String {
    try await Task.sleep(nanoseconds: 3_000_000_000) //3초
    return "Sleep End"
  }

  // 출력 결과
  // "A"
  // "B"
  // ~ 3초 후 ~
  // "Sleep End"
  ```
  
</details>

<details> 
  <summary> Auto Layout의 장단점은? </summary>

  ```

  ```
  
</details>

<details> 
  <summary> KVC와 KVO란? </summary>

  ```

  ```
  
</details>

<details> 
  <summary> Method Swizzling이란? </summary>

  ```

  ```
  
</details>

<details> 
  <summary> HTTP/2의 특징은? </summary>

  ```

  ```
  
</details>

<details> 
  <summary> Memory Leak의 대처방법은? </summary>

  ```

  ```
  
</details>

<details> 
  <summary> 이미지 리스트의 성능 향상법은? </summary>

  ```

  ```
  
</details>

<details> 
  <summary> </summary>

  ```

  ```
  
</details>
  
</details>

## Swift
<details> 
  <summary> Swift의 특징 세 가지 </summary>

  ```
1. Safe (안전성)
  Swift는 개발자의 실수를 엄격한 문법으로 제어하고자 한다.
ex) 옵셔널, guard 문, 내장된 오류 처리(try/catch/throw)


2. Fast (신속성)
Swift는 최초 개념 설정 시점부터 빠르게 동작하도록 만들어졌다.
Swift는 고성능 LLVM 컴파일러 기술을 사용하여 최신 하드웨어를 최대한 활용할 수 있도록 최적화된 기계어 코드로 변환한다.
Swift는 C, C++ 및 Objective-C 언어의 후속 언어로 클래스, 프로토콜, 제네릭과 같은 객체 지향 기능을 제공하므로 Cocoa 및 Cocoa Touch 개발자에게 필요한 성능과 파워를 제공한다.


3. Expressive (더 나은 표현성)
Swift는 계속해서 읽기 좋고 쓰기 좋은 언어로 발전하고 있다
ex) 세미콜론 제거 / 타입 추론(코드를 더 명확하게 만들고 실수를 덜 하도록 도와줌) / 유니코드 표준을 따르는 문자열 (다국어 및 이모티콘 지원) / 가벼운 클로져 구문 작성 가능 등

  ```
  
</details>

<details> 
  <summary> 다중 패러다임 프로그래밍 언어란? </summary>
  
  ```
  다중 패러다임 프로그래밍 언어(= 멀티 패러다임 프로그래밍 언어) 란 하나 이상의 프로그래밍 패러다임을 지원하는 프로그래밍 언어이다.

  Swift는 아래의 프로그래밍 패러다임을 지원한다.
  - 객체 지향 프로그래밍 패러다임
  - 함수형 프로그래밍 패러다임
  - 프로토콜 프로그래밍 패러다임

  ```

</details>

<details> 
  <summary> struct와 class와 enum의 차이를 설명하시오. </summary>
  
  ```
  struct : 상속(x), 값 타입 - 스택에 저장, 
  class : 상속(ㅇ), 참조 타입 - 스택에 포인터/힙에 데이터 저장,
  enum : 상속(x), 참조 타입 - 스택에 포인터/힙에 데이터 저장,
  
  셋의 공통점 : extenstion으로 기능 확장 가능, 프로토콜 채태 가능
  ```
  
</details>

<details> 
  <summary> class의 성능을 향상 시킬수 있는 방법들을 나열해보시오. </summary>
  
  ```
  class에 접근제어자(final, privete)을 사용해 Dynamic Dispatch 메커니즘으로 작동하는 Class를 Static Dispatch 방식으로 작동하게 한다.
  
  Static Dispatch : 앱이 동작하기 전인 컴파일 시점에 호출할 함수를 결정하기 때문에 성능이 좋다.
  Dynamic Dispatch : 컴파일 이후 앱을 실행하는동안인 런타임 시점에 호출하 함수를 결정하기 때문에 성능이 떨어진다.
  ```
    
</details>

<details> 
  <summary> Copy On Write는 어떤 방식으로 동작하는지 설명하시오. </summary>
  
  ```
  Copy On Write
  : Swift의 값 타입은 새로운 변수를 할당하거나 파라미터로 전달될 때 값 복사가 일어난다.
  다만, 이러한 복사 작업은 상당한 시간이 걸리므로 실제 원본이나 복사본이 수정되기 전까지는 복사를 하지 않고 원본 리소스를 공유하다가
  원본이나 복사본에서 수정이 일어날 경우, 그때 복사하는 작업을 하는 기술이다. 
  
  - Swift에선 Collection Type(Array, Dictionary, Set)에만 COW가 적용된다.
  - 사용자 정의 값타입에서는 COW를 지원하지 않지만, 사용자가 직접 COW를 구현할 수 있다.
  ```
  
</details>

<details> 
  <summary> Convenience init에 대해 설명하시오. </summary>
  
  ```
  초기화의 두 가지 종류
  
  - Designated init : 클래스의 모든 프로퍼티 초기화
    init(_ a: String, _ b: String, _ c: String) { 
    }
   
  - Convenience init : Designated init의 파라미터 중 일부를 초기화
    convenience init( _ b: String, _ c: String) {
      self.init("a", b, c)
    }
  ```
  
</details>

<details> 
  <summary> AnyObject에 대해 설명하시오. </summary>
  
  ```
  AnyObject : 모든 클래스 타입을 나타낼 수 있는 프로토콜 
  
  ```
  
</details>

<details> 
  <summary> Singleton 패턴을 활용하는 경우를 예를 들어 설명하시오. </summary>
  
  ```
  iOS에서 Singleton 활용하는 경우 : NotificationCenter, UserDefault, URLCache, URLSession 등
  
  - Singleton의 장점
  1. 인스턴스를 1회만 생성하므로 메모리, 성능 측면에서 효율이 좋다.
  2. 클래스간 데이터 공유가 쉽다.
  3. 인스턴스가 하나라는 것을 보장 -> Thread safe
  
  - Singleton의 단점
  1. 전역적으로 접근할 수 있기 때문에 이에 접근하는 객체를 추적하기 어려워지는 경우가 생긴다.
  
  - Singleton 대안 : DI(의존성 주입)
  
  ```
  
</details>

<details> 
  <summary> KVO 동작 방식에 대해 설명하시오.  </summary>
  
  ```
  KVO(= Key-Value Observing) : 다른 객체의 속성이 변경될 때 객체가 직접 알림을 받을 수 있는 메커니즘
  
  - NSObject를 상속받은 객체에서만 사용 가능
  - Objective-C Runtime에서만 사용이 가능하고, @objc dynamic 붙여서 사용
  - didSet, willSet과 유사하게 동작
  ```
  
</details>

<details> 
  <summary> Delegate와 Notification 방식의 차이점에 대해 설명하시오.  </summary>
  
  ```
  Delegate : 지정된 객체가 해야하는 메소드들의 원형을 프로토콜 형태로 정해놓은 디자인 패턴
  Notification : 서로 데이터를 보내주고 통신할 수 있도록 하기 위해 Notification Center라는 싱글톤 객체를 통해 
  이벤트들의 발생 여부를 옵저버를 등록한 객체들에게 알려주는 것
  
  공통점 : 앱에서 발생한 이벤트가 현재 화면이 아닌 다른 화면까지 영향을 주어야할 때 주로 사용
  
  차이점
  - Delegate : 이벤트의 수신자가 발신자의 정보를 알고 있어야함
  - Notification : 이벤트의 수신자가 발신자의 정보를 몰라도 됨
  
  ```
  
</details>

<details> 
  <summary> Protocol Oriented Programming과 Object Oriented Programming의 차이점을 설명하시오. </summary>
  
  ```
  POP : 프로토콜 중심 프로그래밍
  - 프로토콜 확장을 통한 수평 구조의 타입 확장
  - HAS-A 관계로 표현
  
  OOP : 객체 중심 프로그래밍
  - 상속을 통한 수직 구조의 타입 확장
  - IS-A 관계 표현
  
  Is - A 관계 : 부모 - 자식 간의 상속 관계
  Has - A 관계 : 보유한 기능을 표현하는 포함 관계

  POP vs OOP
  - 다중 상속이 불가능하기 때문에 하나의 타입이 여러 가지 클래스를 상속 받을 수는 없지만, 프로토콜은 다양하게 채택할 수 있어 타입의 기능 확장에 유리하다.
  - 상속은 참조 타입 클래스만 가능하지만, 프로토콜은 struct, class, enum 등의 참조/값 타입을 자유롭게 사용할 수 있다.
  
  ```
  
</details>

<details> 
  <summary> Generic 이란? </summary>

  ```
  Generic : 타입에 의존하지 않는 범용 코드를 작성할 때 사용되는 것

  // 아래와 같이 타입에 제한을 두지 않는 코드를 작성할 수 있다.
  func addTwoValues<T> (_ a: T, _ b:T) -> T {
    return a + b
  }

  여기서 T(Type parameter)는 해당 함수가 실제로 호출될 때 해당 매개변수의 타입으로 대체되는 placeHolder이다.

  제네릭은 위처험 함수 뿐만 아니라 구조체, 클래스, 열거형 타입에도 선언할 수 있다.

  // 구조체
  struct Stack<T> {
      let items: [T] = []
      mutating func push(_ item: T) { ... }
      mutating func pop() -> T { ... }
  }
  ```
</details>

<details> 
  <summary> PropertyWrapper 란? </summary>

  ```
  연산 프로퍼티의 중복되는 로직을 구현하고 해당 로직을 필요로 하는 프로퍼티들 자체에 연결하여 사용할 수 있게 하여 코드의 재사용성을 높일 수 있게 한다.

  struct, class, enum을 만들고 @propertyWrapper 를 맨 앞에 명시하여 정의

  // 정의
  @propertyWrapper
  struct UserDefault<T> {
  }

  // 사용하기
  @UserDefault(key: "isLoggedIn", defaultValue: false)
  static var isLoggedIn: Bool

  ```
</details>


## ARC

<details> 
  <summary> ARC란 무엇인지 설명하시오. </summary>
  
  ```
  ARC : Swift가 제공하는 자동 메모리 관리 도구
  
  - referece count를 관리하고 0이 되면 자동으로 메모리를 해제
  ```
  
</details>

<details> 
  <summary> Retain Count 방식에 대해 설명하시오. </summary>
  
  ```
  Retain Count 방식 : MRC, ARC
  
  - MRC : 객체의 레퍼런스 카운트를 직접 관리하는 방식 -> retain, release 직접 호출
  - ARC : 객체의 레퍼런스 카운트를 iOS가 자동 관리하는 방식 -> retain, release 자동 호출
 
  - Retain : NSObject 클래스 함수로 객체가 메모리에서 해제되지 않도록 래퍼런스 카운트를 증가시킴
  - Release : NSObject 클래스 함수로 객체를 더이상 사용하지 않거나, 메모리에서 해제하고 싶을 때 호출하여 래퍼런스 카운트 감소시킴
  ```
  
</details>

<details> 
  <summary> Strong 과 Weak 참조 방식에 대해 설명하시오. </summary>
  
  ```
  강한 참조 : 인스턴스의 주소값이 변수에 할당될 때 RC가 증가하는 참조 방식
  - 인스턴스를 생성할 때 default가 강한 참조
  - 순환참조 발생할 수 있음 -> 발생 시 메모리 누수 발생
  
  약한 참조 : 인스턴스를 참조할 때 RC를 증가시키지 않는 참조 방식
  - 강한 순화 참조를 해결할 수 있음
  ```
  
</details>

<details> 
  <summary> 순환 참조에 대하여 설명하시오. </summary>
  
  ```
  순환 참조 : 두 개의 객체가 서로가 서로를 참조하고 있는 형태
  => 서로 참조하고 있기 때문에 절대 메모리가 해제되지 않음
  - 메모리 누수 발생 
  ```
  
</details>

<details> 
  <summary> 강한 순환 참조 (Strong Reference Cycle) 는 어떤 경우에 발생하는지 설명하시오. </summary>
  
  ```
  1. 클래스 인스턴스 간의 강한 순환 참조

  2. Escaping 클로저에서의 강한 순환 참조
  non-escaping closure에서는 클로저 내에서 작업을 마치고 메모리가 해지되기 때문에 강한 참조를 해도 상관없지만,
  escaping closure에서는 함수가 종료되어도 참조 카운트가 남아 있어 메모리 누수가 발생할 수 있다.

  따라서, 인스턴스 참조로 인한 강한 순환참조를 업애기 위해 [weak self] 를 사용한다.
  특히, rxSwift의 operator들과 subscriber들은 모두 escaping closure로 되어있기 때문에 [weak self] 를 사용해야한다.
  ```
  
</details>

<details> 
  <summary> weak vs unowned </summary>

  ```
  1. Weak : 약한 참조
  - 참조하는 인스턴스의 참조 횟수를 증가시키지 않음
  - 메모리 해제 시 nil 할당 -> 옵셔널 타입이어야한다.

  2. Unowned :  미소유 참조
  - 참조하는 인스턴스의 참조 횟수를 증가시키지 않음
  - 메모리에서 해제돼도 nil 할당하지 않음 -> 상수 타입

  unowned 객체가 사라지게 되면 댕글링 포인터가 남게 되고, 이 댕글링 포인터를 참조하게 되면 crash 발생
  따라서 unowned는 사라지지 않을 것이라고 보장되는 객체에만 설정해야한다.

  * 댕글링 포인터 : 기존에 바라보고 있던 객체가 해제되면서 할당되지 않는 공간을 바라보는 포인터

  ```

</details>

## 객체지향 프로그래밍(OOP)
<details> 
  <summary> 객체지향 프로그래밍이란? </summary>
  
  ```
  상태와 동작을 포함하고 있는 객체를 정의하고, 객체의 상호작용으로 프로그램을 구성하는 것

  장점 : 코드의 재사용성이 높고, 유지보수가 용이하다
  단점 : 높은 설계 역량이 요구되고, 코드가 복잡해진다. 의존관계로 인해 절차지향 프로그래밍보다 대체로 속도가 느리다
  ```
  
</details>

<details> 
  <summary> 객체지향 프로그래밍의 네 가지 특성 </summary>
  
  ```
  1. 추상화
  : 객체의 공통적인 기능이나 속성을 추출하여 정의하는 것
  ex) 프로토콜, 클래스

  2. 상속성
  : 자식 클래스가 부모 클래스를 상속받을 수 있는 것
  자식 클래스는 부모 클래스의 모든 기능과 속성을 간펴하게 사용할 수 있다.

  3. 다형성
  : 자식 클래스는 override를 통해 상속받은 부모 클래스의 기능을 수정하여 사용할 수 있다.

  4. 캡슐화
  : 클래스 안의 연관 기능이나 속성을 캡슐화 하여 외부로 부터 보호하는 것

   - 데이터 보호 : 외부로부터 클래스에 정의된 기능이나 속성을 보호
   - 데이터 은닉 : 외부에 내부의 동작을 감추고 필요한 부분만 노출
  ```
  
</details>

<details> 
  <summary> 객체지향 프로그래밍의 5대 원칙 </summary>
  
  ```
SOLID

1. SRP, 단일 책임의 원칙
: 하나의 클래스는 하나의 기능만 수행하도록 하는 원칙

2. OCP, 개방-폐쇄 원칙
: 확장에서는 열려있고, 수정에는 닫혀있는 원칙

3. LSP, 리스코프 치환의 원칙
: 부모클래스를 상속받은 자식클래스가 있을 때, 부모 클래스를 호출하는 동작에서 자식클래스가 부모 클래스를 완전히 대체할 수 있다는 원칙

4. ISP, 인터페이스 분리의 원칙
: 하나의  일반적인 인터페이스보다 여러개의 구체적인 인터페이스가 낫다는 원칙

5. DIP, 의존성 역전의 원칙
: 객체는 구체적인 것이 아니라 추상적인 것에 의존해야한다는 원칙으로 상위 레벨의 모듈이 하위 레벨에 의존하게되는 위계관계를 끊는 원칙

상위 레벨의 모듈이 하위 레벨의 모듈에 의존하지 않도록 상위레벨에서 추상화된 인터페이스(=프로토콜)을 정의하고, 하위레벨이 이 프로토콜을 따르도록 한다.
  ```
  
</details>

## iOS의 디자인 패턴

<details> 
  <summary> MVC 패턴 </summary>

  ```
  Model(모델), View(뷰), Controller(컨트롤러) 로 구성된 패턴

  - Model : 데이터 및 비즈니스 로직 관리
  - View : 사용자에게 보여지는 UI
  - Controller : 사용자의 입력을 받고 처리

  Controller로 사용자의 입력이 들어오면 Model을 통해 데이터를 업데이트 하거나 불러오고, 해당 데이터를 보여줄 View를 선택해서 화면에 보여준다.

  그러나, 실제 iOS에서는 Controller의 역할을 ViewController가 당당하고, View가 ViewController 내에 있기 때문에
  View와 Controller가 강하게 연결되어 있고 View Controller가 거의 모든 일을 하게 된다.
  따라서 실제로는 Model만 따로 만들어지게 된다.
  ```
  
</details>

<details> 
  <summary> MVP 패턴 </summary>

  ```
  Model, View, Presenter 로 구성된 패턴

  - Model : 데이터 및 비즈니스 로직 관리
  - View : 사용자에게 보여지는 UI
  - Presenter : View에서 요청한 정보를 Model로부터 가공해서 View로 전달

  View로 사용자의 입력이 들어오면 Presenter에 작업을 요청하고, Presenter는 필요한 데이터를 Model에 요청한다.
  이후 Model로부터 업데이트 된 데이터를 전달받아 View를 갱신한다.

  MVP에서는 View와 ViewController 모두 View 계층에 해당한다.

  ```
  
</details>


<details> 
  <summary> MVVM 패턴 </summary>

  ```
  Model, View, ViewModel 로 구성된 패턴

  - Model : 데이터 및 비즈니스 로직 관리
  - View : 사용자에게 보여지는 UI
  - ViewModel : View를 위한 Model로 View와 Binding을 하여 연결 후 View의 액션을 받고 View를 업데이트 함

  View로 사용자의 입력이 들어오면 ViewModel에 명령을 하고, ViewModel은 필요한 데이터를 Model에 요청한다.
  이후 응답받은 데이터를 가공해서 저장하고, View는 ViewModel과의 Data Binding으로 인해 자동으로 갱신된다.

  ```
  
</details>






