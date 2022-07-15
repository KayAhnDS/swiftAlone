# Protocol - CustomStringConvertible

```swift
class Shoe {
  let color: String
  let size: Int
  let hasLaces: Bool

init(color: String, size: Int, hasLaces: Bool) {
  self.color = color
  self.size = size
  self.hasLaces = hasLaces
  }
}
 
let myShoe = Shoe(color: "Black", size: 12, hasLaces: true)
let yourShoe = Shoe(color: "Red", size: 8, hasLaces: false)
print(myShoe)
print(yourShoe)
```

- 이런 상황(객체의 정보를 보고싶은 상황)에서 print(myShoe)와 print(yourShoe)를 하게되면 “Shoe”라는 결과값을 얻는다.
- CustomStringConvertible 프로토콜은 이런 상황을 위해 만들어졌다!
- CustomStringConvertible프로토콜은 필수로 인스턴스의 정보를 String 타입으로 리턴하는 description이라는 하나의 연산 프로퍼티를 구현해야한다.

# 첫째

- 프로토콜을 채택한다

```swift
class Shoe: CustomStringConvertible {
  let color: String
  let size: Int
  let hasLaces: Bool
}
```

# 둘째.

- 필수 메서드나 변수를 추가해 프로토콜을 준수한다.
- 현재의 경우에는 description 연산 프로퍼티를 추가한다.
    - 해당 스텝을 준수하지 않으면 컴파일러는 준수하지 않았다는 에러를 표시한다.

```swift
class Shoe: CustomStringConvertible {
    let color: String
    let size: Int
    let hasLaces: Bool
 
    init(color: String, size: Int, hasLaces: Bool) {
        self.color = color
        self.size = size
        self.hasLaces = hasLaces
    }
 
    var description: String {
        return "Shoe(color: \(color), size: \(size), hasLaces: \
        (hasLaces))"
    }
}

let myShoe = Shoe(color: "Black", size: 12, hasLaces: true)
let yourShoe = Shoe(color: "Red", size: 8, hasLaces: false)
print(myShoe)
print(yourShoe)
```

```swift
콘솔로 나오는 결과:
Shoe(color: Black, size: 12, hasLaces: true)
Shoe(color: Red, size: 8, hasLaces: false)
```

- CustomStringConvertible을 채택하고 준수했을때 해당 인스턴스를 print()메서드로 부르면 위의 결과처럼 이니셜라이저 처럼 나오는것을 확인할 수 있는데 이것은 사용자에게 좀 더 정확한 정보를 전달하기 위함이다.

#### 출처: Develop in Swift Data Collections Xcode 13
