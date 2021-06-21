# JSON_Parsing_Study

## JSON이란?
- JSON (JavaScript Object Notation)
  - Key, Value 쌍으로 이루어진 데이터 오브젝트를 전달하기 위해 사용하는 개방형 표준 포맷
```json
{
  "name": "손흥민",
  "age": 30,
  "job": "Football Player",
  "martial_status": false,
  "hobby": null,
  "current_club": "Tottenham Hotspur",
  "before_clubs": ["Hamburger SV", "Bayer 04 Leverkusen"]
}
```

## Parsing
```swift
let json: String = """
{
  "name": "손흥민",
  "age": 30,
  "job": "Football Player",
  "martial_status": false,
  "hobby": null,
  "current_club": "Tottenham Hotspur",
  "before_clubs": ["Hamburger SV", "Bayer 04 Leverkusen"]
}
"""
```

### Codable
- Model에 Codable 프로토콜을 채택함으로써, json의 데이터를 직접 매칭시키는 작업없이 손쉽게 Decode하는 것이 가능
- CodingKey 프로토콜을 이용해 json의 Key 값과 사용자가 정의한 Property를 일치시킬 수 있다!

```swift
struct FootballPlayer: Codable {
  let name: String
  let age: Int
  let job: String
  let martialStatus: Bool
  let hobby: String? // nil이 발생할 수 있는 경우, Type을 Obtional로 선언해줘야 에러가 발생하지 않는다!
  let currentClub: String
  let beforeClubs: [String]
  
  enum CodingKeys: String, CodingKey {
    case name, age, job, hobby
    case martialStatus = "martial_status"
    case currentClub = "current_club"
    case beforeClubs = "before_clubs"
  }
}

func parse() {
  let decoder = JSONDecoder()
  let data = json.data(using: .utf8)
  
  if let data = data, let footballPlayer = try? decoder.decode(FootballPlayer.self, data: data) {
    // To do
  }
}
```
