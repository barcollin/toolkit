# Golang toolkit

A simple go module that provides commonly used go-tools 

## Features

* **Random String Generator** - Generates random string of `n` lenght based on these characters `abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_`
* **Files Upload** - Upload files and generate random filenames using `Random string Generator` , it also support file size limits and file types customization
* **Creating Directory** - Create directories it they don't exist
* **Generating Slugs** - Generate slugs from a string

## Installation

```go get -u github.com/barcollin/toolbox```

## Examples

#### Random String Generation

```go
package main

import (
	"fmt"

	"github.com/barcollin/toolkit"
)

func main() {
	var tools toolkit.Tools

	s := tools.RandomString(20)

	fmt.Println("Random string:", s)

}
```

#### Creating a Directory if it doesn't exist

```go
package main

import (
	"github.com/barcollin/toolkit"
)

func main() {
	var tools toolkit.Tools

	tools.CreateDirIfNotExist("./test-dir")
}

```