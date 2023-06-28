
# 문자열

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
	- ReversedCollection 타입을 리턴한다. -> 반복문으로 사용

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
