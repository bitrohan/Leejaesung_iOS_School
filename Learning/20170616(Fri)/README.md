# 패스트캠퍼스 강의 노트 28th ( 20170616 )

# 오늘의 팁

## `PairProgramming` Code Review Day

 - 버튼을 눌러서 segue를 태우는 로직에서 예외처리를 할 때, `performSegue(withIdentifier identifier: String, sender: Any?)`을 이용해서 처리를 하도록 하자.
 - 함수의 input과 output을 잘 설계해서, output의 타입을 꼭 필요한 타입으로 return하도록 하자. ( UInt32 등등 )


# 예외처리

## Error

```swift
enum VendingMachineError: Error {
```

## 에러 전달

```swift
//에러전달 가능성 함수
```


## 에러 처리
 - 함수가 에러를 throw하면 프로그램의 흐름이 변경되므로 에러 가 발생할 수있는 코드의 위치를 신속하게 식별 할 수 있어야합 니다.

예제 참고: [애플 공식 문서](https://developer.apple.com/library/content/documentation/Swift/Conceptual/Swift_Programming_Language/ErrorHandling.html)


## Converting Errors to Optional Value

func someThrowingFunction() throws -> Int {


}
```

## Specifying Cleanup Actions (후처리)
 - `defer`
 - 함수가 종료되더라도 defer는 꼭 실행되고, 아래의 defer부처 실행된다.

```swift
}
```

# Singleton

## `Singleton`이란?
 - 어플리케이션 전 영역의 걸쳐 하나의 클래스의 단 하나의 인스턴스만(객체)을 생성하는 것을 싱글톤 패턴이라고 한다.
 - 사용 이유: 애플리케이션 내부에서 유일하게 하나만 필요한 객체에서 사용.
 - 클래스 메소드로 객체를 만들며 `static`을 이용해서 **단 1개의 인스턴스** 만 만든다.
 - **앱 내에서 공유하는 객체** 를 만들 수 있다.
 - 물론, 앱이 종료되면 사라진다.
 - `Singleton Pattern`은 일종의 디자인 패턴으로 JAVA, Obj-C 등 객체지향 언어에서도 다루고 있다.

### 싱글톤 문법

```swift
class SingletonClass {
    
```

### Function & Method
 - `함수`는 인스턴스를 만들지 않아도 사용할 수 있다. ( ex. `print()` )
 - `메소드`는 인스턴스를 만들어야지만, 사용할 수 있는 것을 메소드라고 한다.

```swift
import Foundation

func function2DA() {
	// 파일 안에 있을 뿐, 별도 클래스 안에 있지 않은 것이 함수.
	// Objective-C에서는 불가능했다. Swift는 함수형 프로그래밍이 가능하기 때문에 허용!
}

class SampleClass {
	static func typeMethod() {
		//클래스 안에서 만든 것이 메소드
	}
}
```
```swift
class main {

	function2DA()
	//...//
	
	SampleClass.typeMethod()
	//...//
	
}
```

## Singleton Pattern 예제

```swift
//스크린 정보를 가지고 있는 객체

```

### [예제] 재성이 만든 예제
 - 뷰를 이동할 때, 싱글턴 데이터를 가지고 이동하기.

```swift
class DataCenter {
    static var sharedData:DataCenter = DataCenter()
    
    var textData:String = String()   
}
```

```swift
class SecondViewController: UIViewController {
    
    @IBOutlet var textfieldInput:UITextField?
    @IBOutlet var labelData:UILabel?

    override func viewDidLoad() {
        super.viewDidLoad()

        labelData?.text = DataCenter.sharedData.textData
        
    }
    
// ... //

    @IBAction func buttonAction(_ sender:UIButton) {
        
        DataCenter.sharedData.textData = DataCenter.sharedData.textData + (textfieldInput?.text ?? "test")
        
    }
```

### 문서 끝 ( by 재성 )