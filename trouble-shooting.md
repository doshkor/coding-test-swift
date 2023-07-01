# 코딩테스트 문제풀이

### 그룹 단어 체커
- 백준 1316
- https://www.acmicpc.net/problem/1316
- 그룹 단어란 단어에 존재하는 모든 문자에 대해서, 각 문자가 연속해서 나타나는 경우만을 말한다. 
- 예를 들면, ccazzzzbb는 c, a, z, b가 모두 연속해서 나타나고, kin도 k, i, n이 연속해서 나타나기 때문에 그룹 단어이지만, aabbbccb는 b가 떨어져서 나타나기 때문에 그룹 단어가 아니다.
- 단어 N개를 입력으로 받아 그룹 단어의 개수를 출력하는 프로그램을 작성하시오.

- 필요한 로직 및 아이디어
	- 연속으로 같은 알파벳이 나오는 것만 가능해야 한다.
	- 체크를 할 수 있는 배열을 만든다
	- ⭐️분기 처리
		- 체크 배열에 없는 경우(알파벳이 처음인 경우)
		- 체크 배열에 있는 경우
			- 지금 넣고있는 중인 경우(`array.last == currentAlphabet`)
			- 지금 넣고 있는 중이 아닌 경우
``` Swift
import Foundation

let number = Int(readLine()!)!
var count = 0
for _ in 1...number {
    let input = readLine()!

    var isError = false
    var checker: [Character] = []

    for char in input {
        if !checker.contains(char) {
            checker.append(char)
        }
        else if checker.last == char {
            continue
        }
        else {
            isError = true
            break
        }
    }
    
    if isError {}
    else {
        count += 1
    }
}

print(count)

```



# 메서드

### String[index] 타입

- "someString" 의 맨 앞 문자와 맨 뒤 문자를 합친 결과를 출력한다
- ex) "someString" -> "sg"

시도
- `String[Index]`를 활용하여 얻은 문자 두 개를 더해서 출력하고자 하였다

```Swift
let someString = "someString"

let firstIndex = someString.startIndex
let lastIndex = someString.index(someString.endIndex, offsetBy: 1)

🔴 print(someString[firstIndex] + someString[lastIndex])
```

문제점
- `String[Index]` 를 사용하면 Character 값을 리턴한다.
- Character 타입은 + 연산이 불가능하다

해결 방법
- `"".append()` 를 사용하였습니다.
