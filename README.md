# JSON_Parsing_Study

## JSON이란?
- JSON (JavaScript Object Notation)
  - Key, Value 쌍으로 이루어진 데이터 오브젝트를 전달하기 위해 사용하는 개방형 표준 포맷
```json
// Ref.: https://yohanpro.com/posts/js/JSONType

{
  "String": "hello world",
  "Number": 3.14159,
  "Null": null,
  "Boolean": true,
  "Array": [20, 30, "orange"],
  "Object": {
    "name": "Yohan",
    "age": "28"
  }
}
```

## Parsing

### Codable
- Model에 Codable을 채용함으로써, json의 데이터를 직접 매칭시키는 작업없이 손쉽게 파싱을 진행하는 것이 가능

