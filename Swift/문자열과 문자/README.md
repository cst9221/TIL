### 출처
[The Swift Language Guide (KR)](https://jusung.gitbook.io/the-swift-language-guide/language-guide/02-basic-operators)의 내용을 인용하였습니다. 가이드가 상당히 괜찮으니 가이드를 꼭 읽으시길..

### 문자열 리터럴
```let something = "Some string literal value"```

```"""```로 여러줄을 작성가능
```
let quotation = """
The White Rabbit put on his spectacles.  "Where shall I begin,
please your Majesty?" he asked.
"Begin at the beginning," the King said gravely, "and go on
till you come to the end; then stop."
"""
```
``` \```로 줄바꿈
```
let softWrappedQuotation = """
The White Rabbit put on his spectacles.  "Where shall I begin, \
please your Majesty?" he asked.
"Begin at the beginning," the King said gravely, "and go on \
till you come to the end; then stop."
"""
```
들여쓰기
```
let linesWithIndentation = """
----This line doesn't begin with whitespace.
--------This line begins with four spaces.
----This line doesn't begin with whitespace.
----"""
```
특수문자 사용가능 (```\0```, ```\t```, ```\n```, ```\r```, ```\"```, ```\'```, )
```\u{n}```, n은 1-8자리 십진수 형태로 구성된 유니코드
```
let wiseWords = "\"Imagination is more important than knowledge\" - Einstein"
// "Imagination is more important than knowlege" - Einstein
let dollaSign = "\u{24}"            // $, 유니코트 U+0024
let blackHeart = "\u{2665}"         // ♥, 유니코드 U+2665
let sparklingHeart = "\u{1F496}" // 💖,유니코드 U+1F496
```

### 빈 문자열 초기화
두 값은 같음
```
var emtpryString = ""
var anotherEmptyString = String()

// 빈 문자열인지 확인
if emptyString.isEmpty {
    print("Nothing to see here")
}

// 수정
var variableString = "Horse"
variableString += " and carriage"
// variableString = Horse and carriage

let constantString = "Highlander"
constantString += " and another Highlander"
// 문자열 상수(let)로 선언돼 있어 에러발생!
```

### 값 타임 문자열
Swift의 String은 값 타입(value type)입니다. 그래서 String이 다른 함수 혹은 메소드로 부터 생성되면 String값이 할당 될때, 이전 String의 레퍼런스를 할당하는 것이 아니라 값을 복사해서 생성합니다. 반대로 이야기 하면 다른 메소드에서 할당 받은 문자열은 그 문자열을 수정해도 원본 문자열이 변하지 않기 때문에 편하게 사용하셔도 됩니다.
값 <-> 참조

### 문자
문자열의 개별 문자를 ```for-in```로 사용 가능
```
for character in "Dog!🐶" {
    print(character)
}
// D // o // g // ! // 🐶


let exclamationMark: Character = "!"    // 상수로 사용가능

let catCharacters: [Character] = ["C", "a", "t", "!", "🐱"]
let catString = String(catCharacters)
print(catString)
// Prints "Cat!🐱"
```
