##### 출처
[The Swift Language Guide (KR)](https://jusung.gitbook.io/the-swift-language-guide/language-guide/05-control-flow)의 내용을 인용하였습니다. 가이드가 상당히 괜찮으니 꼭 읽으시길..

```while loop```, ```if guard```, ```switch```, ```for-in``` 등 다양한 제어문 제공

### For-In 문 (For-In Loops)
```for-in```문는 배열, 숫자, 문자열을 순서대로 순회할 때 사용됨
```swift
let names = ["Anna", "Alex", "Brian", "Jack"]
for name in names {
    print("Hello, \(name)!")
}
// Hello, Anna!
// Hello, Alex!
// Hello, Brian!
// Hello, Jack!
```

dictionary에서 반환된 key-value 쌍으로 구성된 튜플을 순회할 수도 있다. 
```swift 
let numberOfLegs = ["spider": 8, "ant": 6, "cat": 4]
for (animalName, legCount) in numberOfLegs {
    print("\(animalName)s have \(legCount) legs")
}
// ants have 6 legs
// spiders have 8 legs
// cats have 4 legs
// dictionary에 담긴 콘텐츠는 정렬이 되지 않은 상태, 사전에 넣었던 순서대로 순회되지 않습니다. 
```
아래와 같이 숫자 범위를 지정해 순회할 수 있습니다.
```swift 
for index in 1...5 {
    print("\(index) times 5 is \(index * 5)")
}
// 1 times 5 is 5
// 2 times 5 is 10
// 3 times 5 is 15
// 4 times 5 is 20
// 5 times 5 is 25
```

```for-in``` 문을 순서대로 제어할 필요가 없다면, 변수자리에 _키워드를 사용하여 성능을 높일 수 있다.

```swift
let base = 3
let power = 10
var answer = 1
for _ in 1...power {
    answer *= base
}
print("\(base) to the power of \(power) is \(answer)")
// Prints "3 to the power of 10 is 59049"
```
범위 연산자와 함께 사용할 수 있다.
```swift 
let minutes = 60
for tickMark in 0..<minutes {
    // render the tick mark each minute (60 times)
}
```
[stride(from:to:by:)](https://developer.apple.com/documentation/swift/1641347-stride) 함수와 함께 사용할 수 있다.
```swift 
// stride 구간이 5일 때
let minuteInterval = 5
for tickMark in stride(from: 0, to: minutes, by: minuteInterval) {
    // render the tick mark every 5 minutes (0, 5, 10, 15 ... 45, 50, 55)
}

// stride 구간이 5일 때
let hours = 12
let hourInterval = 3
for tickMark in stride(from: 3, through: hours, by: hourInterval) {
    // render the tick mark every 3 hours (3, 6, 9, 12)
}
```

### While 문 (While Loops)
Swift에서는 ```while```과 ```repeat-while``` 두 가지 while문을 지원

#### while
조건이 거짓일때까지 구문을 반복합니다.
```swift
while condition {
    statements
}
// condition 조건 
// statements 구문
```
while 문의 (예)
```swift
var square = 0
var diceRoll = 0
while square < finalSquare {
    // roll the dice
    diceRoll += 1
    if diceRoll == 7 { diceRoll = 1 }
    // move by the rolled amount
    square += diceRoll
    if square < board.count {
        // if we're still on the board, move up or down for a snake or a ladder
        square += board[square]
    }
}
print("Game over!")
```

#### Repeat-While 문
reapeat-while문은 다른 언어의 do-while문과 유사함

구문(statements)을 먼저 실행하고 while 조건이 거짓일 때까지 반복
```swift 
repeat {
    statements
} while condition
```
```repeat-while``` 문의 (예)
```swift
repeat {
    // move up or down for a snake or ladder
    square += board[square]
    // roll the dice
    diceRoll += 1
    if diceRoll == 7 { diceRoll = 1 }
    // move by the rolled amount
    square += diceRoll
} while square < finalSquare
print("Game over!")
```




