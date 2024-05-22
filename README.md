# LangDetect

Natural language detection for Go.

## Features
* Supports [84 languages](https://github.com/altuniverse/langdetect/blob/master/SUPPORTED_LANGUAGES.md)
* 100% written in Go
* No external dependencies
* Fast
* Recognizes not only a language, but also a script (Latin, Cyrillic, etc)

## Getting started
Installation:
```sh
    go get -u github.com/altuniverse/langdetect
```

Simple usage example:
```go
package main

import (
	"fmt"

	"github.com/altuniverse/langdetect"
)

func main() {
	info := langdetect.Detect("Test para")
	fmt.Println("Language:", info.Lang.String(), " Script:", langdetect.Scripts[info.Script], " Confidence: ", info.Confidence)
}
```

## Blacklisting and whitelisting
```go
package main

import (
	"fmt"

	"github.com/altuniverse/langdetect"
)

func main() {
	//Blacklist
	options := langdetect.Options{
		Blacklist: map[langdetect.Lang]bool{
			langdetect.Ydd: true,
		},
	}

	info := langdetect.DetectWithOptions("האקדמיה ללשון העברית", options)

	fmt.Println("Language:", info.Lang.String(), "Script:", langdetect.Scripts[info.Script])

	//Whitelist
	options1 := langdetect.Options{
		Whitelist: map[langdetect.Lang]bool{
			langdetect.Epo: true,
			langdetect.Ukr: true,
		},
	}

	info = langdetect.DetectWithOptions("Mi ne scias", options1)
	fmt.Println("Language:", info.Lang.String(), " Script:", langdetect.Scripts[info.Script])
}
```

## Requirements
Go 1.2 or higher

## License
[MIT](https://github.com/altuniverse/langdetect/blob/master/LICENSE)

