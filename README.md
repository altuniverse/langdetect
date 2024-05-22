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
	info := whatlanggo.Detect("Test para")
	fmt.Println("Language:", info.Lang.String(), " Script:", whatlanggo.Scripts[info.Script], " Confidence: ", info.Confidence)
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
	options := whatlanggo.Options{
		Blacklist: map[whatlanggo.Lang]bool{
			whatlanggo.Ydd: true,
		},
	}

	info := whatlanggo.DetectWithOptions("האקדמיה ללשון העברית", options)

	fmt.Println("Language:", info.Lang.String(), "Script:", whatlanggo.Scripts[info.Script])

	//Whitelist
	options1 := whatlanggo.Options{
		Whitelist: map[whatlanggo.Lang]bool{
			whatlanggo.Epo: true,
			whatlanggo.Ukr: true,
		},
	}

	info = whatlanggo.DetectWithOptions("Mi ne scias", options1)
	fmt.Println("Language:", info.Lang.String(), " Script:", whatlanggo.Scripts[info.Script])
}
```

## Requirements
Go 1.2 or higher

## License
[MIT](https://github.com/altuniverse/langdetect/blob/master/LICENSE)

