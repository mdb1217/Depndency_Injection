# DI(Dependency Injection) 의존성 주입

#### 1. 의존성 주입이란?

**하나의 객체가 다른 객체의 의존성을 제공하는 테크닉이다.** 

:arrow_right: 일반적으로 클래스 내부에서 객체를 생성하지 않고 외부에서 객체를 생성해 주입 받는 방식을 DI라고한다. DI를 사용하면 **클래스 간의 결합도를 낮추어 의존성을 줄일 수 있고**, 한 클래스를 수정했을 때  다른 클래스도 수정해야 하는 상황을 막아줄 수 있음.

<img src="https://spoqa.github.io/images/2020-11-02/dependency_injection.png"  width="1000" height="400">  

**안드로이드에서 가능한 두 가지 방식의 의존성 주입** 

- 생성자 주입(constructor injection) : 생성자를 통해 의존하는 객체 전달
- 필드 주입(Field Injection) : 객체가 초기화 된 후에 의존하는 객체 전달.



#### 2. 의존성 주입이 필요한 이유

:one: ​**의존 관계 설정이 컴파일시가 아닌 실행시에 이루어져 모듈간의 결합도를 낮출 수 있다.**

:two: **코드의 재사용을 높여서 작성된 모듈을 여러 곳에서 소스코드의 수정 없이 사용할 수 있다.** 

:three: ​**단위 테스트의 편의성을 높여준다.**

:four: **리팩토링이 수월하다.**

:five: **객체 간의 의존성(종속성)을 줄이거나 없앨 수 있음.**

:six: ​**스코프를 이용한 객체 관리**



💡일일히 DI하기엔 복잡하고 힘들어서 보통 라이브러리를 쓰는게 일반적이다. 안드로이드에서는 **`Dagger2`** 와 **`Koin`** 이 대표적인 의존성 주입 라이브러리이다.



#### 3. Dagger2와 Koin

###### :apple: Dagger2

- `java`와 `Android`를 위해 완전히 정적으로 만들어진 컴파일 타임 의존성 주입 프레임 워크
- 리플렉션을 사용하지 않고 컴파일 타임에 코드를 생성해내기 때문에 빠른 속도를 가진다는 장점이 있음.
- 오류의 추적이 쉬움.

###### :green_apple: Koin

- 순수 코틀린만으로 작성이 되어있어서 러닝 커브가 낮음.
- 어노테이션(@) 프로세싱 및 리플렉션을 사용하지 않기 때문에 상대적으로 가벼움.
- `ViewModel` 아키텍처를 위한 별도의 라이브러리를 제공해서 쉽게 `MVVM` 패턴을 만들 수 있음. 
- `Activity`나 `Fragment`, `Service` 등이 아닌 곳에서 사용하기 위해선 생성자로 넘기거나 별도의 구현을 해야함. 
- 아직 UI의 Controller별 Scope 관리 및 Compile 시간에 오류를 확인하는 등의 기능은 Dagger에 비해서 뒤떨어지는 측면이 있음.(물론 유닛테스트를 통해 Runtime시 에러가 발생하는 것을 방지할 수는 있음.)
