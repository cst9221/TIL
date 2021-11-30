### 출처
[The Swift Language Guide (KR)](https://jusung.gitbook.io/the-swift-language-guide/language-guide/02-basic-operators)의 내용을 인용하였습니다. 가이드가 상당히 괜찮으니 가이드를 꼭 읽으시길..

### 할당 연산자
값을 초기화하거나 변경할 때 사용
~~~
let b = 10
var a = 5
a = b     // a 값은 10

let (x, y) = (1, 2) // 튜플을 이용해 여러값 할당 가능 (x는 1, y는 2)

if x = y {
    // error x = y는 값을 반환하지 않음 
    // ==와 =을 구분하여 실수를 막기위함
} 
~~~
### 사칙 연산자
(+, -, *, /)기본적인 사칙 연산자를 제공하며 (%)나머지, (-)음수, (+)양수 연산자도 제공합니다.
```
1 + 2                 // 3
5 - 3                 // 2
2 * 3                 // 6
10.0 / 2.5             // 4.0

"hello, " + "world!"         // "hello, world!"

9 % 4                 // 1
-9 % 4                 // -1

let three = 3
let minusThree = -three        // minusThree = -3
let plusThree = -minusThree    // plusThree = 3(--3)

let micusSix = -6
let alsoMinusSix = +minusSix    // alsoMinusSix = -6
```
### 합성 할당 연산자
+=, -= 같은 할당 연산(=) 사칙 연산(+)형태의 연산자 제공
```
var a = 1
a += 2 // a = 3
```
> **주의 **
합성 할당 연산자는 값을 반환하지 않음

### 비교연산자
==, !=, >, <, >=, <= 일반적인 비교연산자 모두 제공
> **주의**
객체 비교를 위해서는 식별 연산자(===, !==)를 제공함

```
1 == 1    // true
2 != 1    // true
2 > 1    // true
1 < 2    // true
1 >= 1    // true
2 <= 1    // true
```
같은 타입의 값을 갖는 두 개의 튜플을 비교할 수 있다. 비교는 좌에서 우로 한 개씩 비교한다. 
```
(1, "zebra") < (2, "apple")   // true, 1이 2보다 작음. zebra와 apple은 비교하지 않음
(3, "apple") < (3, "bird")    // true 왼쪽 3이 오른쪽 3과 같음. apple은 bird보다 작음
(4, "dog") == (4, "dog")      // true 왼쪽 4는 오른쪽 4와 같음. 왼쪽 dog는 오른쪽 dog와 같음
```
비교 불가능한 경우
```
("blue", false) < ("purple", true)     // 에러, Boolean 값은 < 연산자로 비교할 수 없음
```
> **주의**
Swift 표준 라이브러리에서는 7개 미만의 요소를 가진 튜플만 비교가능함.

### 삼항 조건 연산자
삼항 연산자는 다음과 같은 형태. 코드를 줄여줌으로 가독성을 높일 수 있음
```
question ? answer1 : answer2
```
### Nil 병합 연산자
```a ?? b``` 의 형태를 가짐. ```a != nil ? a! : b```와 같은 코드라고 보면됨
```
let defaultColorName = "red"
var userDefinedColorName: String?    // nil

var colorNameToUse = userDefinedColorName ?? defaultColorName
// userDefinedColorNam은 defaults값인 nil이므로 colorNameToUse 값은 defaultColorName인 red임

userDefinedColorName = "green"
colorNameToUse = userDefinedColorName ?? defaultColorName
// userDefinedColorName가 nil이 아니므로 colorNameToUse는 green이 됨
```

### 범위 연산자
```a...b```의 형태를 가짐. 범위를 나타내며 for-in loop에 주로 사용
```
for index in 1...5 {
    print("\(index) times 5 is \(index * 5)")
}
// 1 times 5 is 5
// 2 times 5 is 10
// 3 times 5 is 15
// 4 times 5 is 20
// 5 times 5 is 25

let names = ["Anna", "Alex", "Brian", "Jack"]
let count = names.count
for i in 0..<count {
    print("Person \(i + 1) is called \(names[i])")
}
// Person 1 is called Anna
// Person 2 is called Alex
// Person 3 is called Brian
// Person 4 is called Jack

for name in names[2...] {
    print(name)
}
// Brian
// Jack

for name in names[...2] {
    print(name)
}
// Anna
// Alex
// Brian

for name in names[..<2] {
    print(name)
}
// Anna
// Alex

let range = ...5
range.contains(7)   // false
range.contains(4)   // true
range.contains(-1)  // true
```

### 논리 연산자
```!a```, ```a && b```, ```a || b```를 제공함
```
let allowedEntry = false
if !allowedEntry {
    print("ACCESS DENIED")
}
// Prints "ACCESS DENIED"

let enteredDoorCode = true
let passedRetinaScan = false
if enteredDoorCode && passedRetinaScan {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// Prints "ACCESS DENIED"

let hasDoorKey = false
let knowsOverridePassword = true
if hasDoorKey || knowsOverridePassword {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// Prints "Welcome!"

if enteredDoorCode && passedRetinaScan || hasDoorKey || knowsOverridePassword {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// Prints "Welcome!"

if (enteredDoorCode && passedRetinaScan) || hasDoorKey || knowsOverridePassword {
    print("Welcome!")
} else {
    print("ACCESS DENIED")
}
// Prints "Welcome!"
```
