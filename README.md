# 문자열


### `# replacingOccurrences(of:with:)`

- 주의점
	- ⭐️ `import Foundation` 을 명시해야 했다(백준 코딩테스트)

```Swift
let input = "apple"
let changedInput = input.replacingOccurrences(of:"p", with:"*")
print(changedInput)
// a**le
```

### `reversed()`

- 문자열이 주어졌을 때 역순으로 배열해보자
```Swift
let myString = "hello"

String(myString.reversed())
// olleh
```

- 123 456 값을 입력 받았을 때, 321 654 로 바꾸고, 최대값을 구하는 방법
``` Swift
let input = readLine()!.split(separator: " ")
// ["123", "456"]
input.map { $0.reversed() }.map { String($0) }.max()!
// 654
```

- 123 456 값을 받았을 때, 321 654 로 바꾸는 방법

### ⭐️ `split()`

> `split(separator: Character, maxSplits: Int = Int.max, omittingEmptySubsequences: Bool = true) -> [Substring]`

- 문자열을 분리하여 배열로 나타낸다.
- 주의점
	- 공백을 기준으로 자를 때, 공백은 여러 개가 있더라도 결과는 같다.

- `split(separator: "")`
```Swift
let myString1 = "hello"
myString1.split(separator: "")
// ["h", "e", "l", "l", "o"]

let myString2 = " he   llo"
myString2.split(separator: "")
// 주의 : "" 로 나눌 때는 공백도 갯수 만큼 그대로 표시된다.
// [" ", "h", "e", " ", " ", " ", "l", "l", "o"]
```

- `split(separator: " ")`
```Swift
let myString1 = "hi how are you"
let myString2 = "  hi how are you"
let myString3 = "hi how    are you "
let myString4 = " hi how are   you  "

// 띄어쓰기는 여러번을 해도 결과는 같다.
// ["hi", "how", "are", "you"]
```


### Int()

- 문자를 숫자로 바꾸는 경우 `character` 를 `string` 으로 바꿔야 합니다.

```Swift
let input: Character = "3"
print(Int(input))
// 🔴 error

let stringValue = String(input)
print(Int(stringValue))
// 3

```

### asciiValue

> `var asciiValue: UInt8? { get }`

- 알파벳 소문자, 대문자, 숫자 0-9중 하나가 주어졌을 때, 주어진 글자의 아스키 코드값을 출력합니다.
- 주의점
	- Optional

```Swift
let input = readLine()!
let characterValue = Character(input)
print(characterValue.asciiValue!)
```

### ` max(), min()`

> `max() -> Self.Element`
> `min() -> Self.Element`

- 문자열에서도 최대값, 최소값을 구할 수 있다.
- 숫자인 문자 경우도 당연히 가능하다.
- 주의점
	- Optional

```Swift
let values = ["1", "2", "3"]
let maxValue = values.max()
print(maxValue!)
// 3

let values = ["ㄱ", "ㄴ", "ㄷ"]
let maxValue = values.max()
print(maxValue!)
// ㄷ


```


### `String[index]`

- 문자열에서 특정 인덱스의 문자를 구할 수 있습니다.
- 주의점 
	- `startIndex` 를 넣어주어야 하고, `firstIndex` 가 아님에 주의

```Swift
let myString = "swift"

let stringIndex = myString.index(myString.startIndex, offsetBy: 2)

print(myString[stringIndex]) 

// 결과값
// i
```



# 배열

### `반복문`

- `index`가 먼저 나온다.! 그리고 `enumerated()`에 유의하자!
```Swift
let myArray = ["apple", "banana"]
for (index, element) in myArray.enumerated() {
	print(index, element)
}
// 0 apple
// 1 banana
```




### `swapAt(i: Int, j: Int)`

- 배열의 요소를 서로 바꿀 때 사용합니다.

```Swift
let numbers = [1, 2, 3, 4]

numbers.swapAt(1, 2)

print(numbers)
// [1, 3, 2, 4]
```

응용 

- [1, 2, 3, 4, 5, 6, 7] 에서 2 ~ 6번째 요소를 역순으로 배열하세요 
- 목표 : [1, 6, 5, 4, 3, 2, 7]

```Swift
var numbers = [1, 2, 3, 4, 5, 6, 7]

var startIndex = 1 // 2 번째의 인덱스는 1 이므로
var endIndex = 5

while startIndex < endIndex {
	numbers.swapAt(startIndex, endIndex)
	startIndex += 1
	endIndex -= 1
}
```

### `reverse()`

- 배열을 반전시킬 때 사용합니다.
- 특징
	- O(n)

```Swift
var a = [1, 2, 3, 4, 5]

numbers.reverse()

print(numbers)
// [5, 4, 3, 2, 1]
```


### `reversed()`

> `reversed() -> ReversedCollection<Array<Element>>`

- 특징
	- O(1)
	- 하지만 반복문을 사용하면 결국 O(n)이다
- 주의점
	- ReversedCollection 타입을 리턴한다. -> 반복문으로 사용, 혹은 Int() 로 변환 가능

```Swift
let numbers = [1, 2, 3, 4, 5]

let x = numbers.reversed()

print(x)
// ReversedCollection<Array<Int>>(_base: [1, 2, 3, 4, 5, 6, 7])
```


### `removeAll(where:)`

- 배열에서 특정한 요소를 제거하고 싶을 때 사용합니다.
- 주의점
	- 리턴값 없이 바로 삭제된다.

```Swift

let numbers = [1, 2, 3]

numbers.removeAll { $0 == 2 }

print(numbers)
// [1,3]
```


### index(before:)

> `index(before: String.Index) -> String.Index`

- 문자열의 마지막 Character 를 얻고 싶을 때 사용합니다.
- 주의점
	- `String.endIndex` 는 `String[]`으로 바로 접근할 수 없습니다.
	- 예를 들어, 3자리 문자의 `endIndex`는 4를 의미합니다.

```Swift
let hello = "안녕하세요"

let lastIndex = hello.index(before: hello.endIndex)
let lastCharacter = hello[lastIndex]
print(lastCharacter)
// "요"
```


### `firstIndex(of: )`

> `firstIndex(of: ) -> Self.index`

- 배열에서 찾고 싶은 요소의 첫 번째 인덱스를 리턴합니다.
- 주의점 
	- Optional

```Swift
let myNumbers = [1, 2, 3]
let x = myNumbers.firstIndex(of: 1)

let myStrings = ["a", "b", "c"]
let y = myStrings.firstIndex(of: "b")

print(x!, y!)
// 0 1
```


### `joined()`

- 배열을 문자열로 바꿀 때 사용합니다.

```Swift
let myArr = ["s", "w", "i", "f", "t"]
let swift = myArr.joined()

// 결과값
// swift
```

- [1, 2, 3, 4] 에서 "1 2 3 4"를 출력하고 싶은 경우

``` Swift
[1, 2, 3].map{ String($0) }.joined(separator: " ")
```


### `joined(separator: )`

- 배열을 문자열로 바꿀 때 사용합니다.
- 사이사이에 문자나 띄어쓰기를 하고 싶을 때 사용합니다.

```Swift
let myArr = ["s", "w", "i", "f", "t"]

let swift = myArr.joined(separator: "-")

// 결과값
// s-w-i-f-t
```


# 고차함수

### `reduce()`

> `reduce(initialResult: Result, nextPartiaResult: (Result, Int) throws -> Result)`

- 초기값과 배열의 요소를 파라미터로 전달해 사용할 수 있습니다.

```Swift
let numbers = [1, 2, 3]

let result = numbers.reduce(0) { partialResult, element in 
	print(partialResult, element)
	return partialResult + element
}
print(result)
//  0 1
//  1 2
//  3 3
//  6 4
// 10 5
// 15
```


### `map()`



### `filter()`

- 주의점
	- return 값을 던져주므로, 원본 값은 변하지 않습니다.

```Swift
let a = [1,2,3]
let b = a.filter { $0 == 2 }

print(a, b)

// 결과값
// [1, 2, 3] [2]
```
