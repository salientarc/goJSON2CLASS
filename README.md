# goJSON2CLASS

`goJSON2CLASS` is a utility that converts JSON schema to classes

## Requirements

- Go-lang >> **[Installation](https://go.dev/doc/install)**
- Git

## Supported Inputs

- [x] JSON Schema
- [ ] JSON
- [ ] JSON API URLs

## Target Languages

- [x] Rust
- [ ] JavaScript
- [ ] TypeScript
- [ ] Java
- [ ] Go
- [ ] C
- [ ] C++

_If your favorite language is missing- please generate an issue or implement it by yourself._

## Installation
  
```sh
# Clone this repo
>> git clone https://github.com/salientarc/goJSON2CLASS.git
```

```sh
# go inside the directory and run build command
>> cd goJSON2CLASS && go build .
```

```sh
>> ./goJSON2CLASS
Usage: goJSON2TYPES <Schema.json> <Output.rs>
```

## Example

Sample JSON Schema

```json
{
  "title": "Root",
  "properties": {
    "property1": {
      "type": "string"
    },
    "property2": {
      "type": "integer"
    },
    "property3": {
      "type": "object",
      "title": "Property3",
      "properties": {
        "nestedProperty1": {
          "type": "boolean"
        },
        "nestedProperty2": {
          "type": "array",
          "items": {
            "type": "string"
          }
        },
        "nestedProperty3": {
          "type": "string"
        }
      }
    }
  }
}
```

Output

```sh
>> .\goJSON2CLASS.exe .\schema.json output.rs
Done!
```

Generated Rust code

```rs
use serde::{Serialize, Deserialize};

#[derive(Debug, Serialize, Deserialize)]
struct Root {
        #[serde(rename = "property1")]
        property1: String,
        #[serde(rename = "property2")]
        property2: i64,
        #[serde(rename = "property3")]
        property3: Property3,
}

#[derive(Debug, Serialize, Deserialize)]
struct Property3 {
        #[serde(rename = "nestedProperty1")]
        nestedProperty1: bool,
        #[serde(rename = "nestedProperty2")]
        nestedProperty2: Vec<String>,
        #[serde(rename = "nestedProperty3")]
        nestedProperty3: String,
}
```

## LICENSE

[GPL](./LICENSE)
