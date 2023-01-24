# Golang toolkit

A simple go module that provides commonly used go-tools 

## Features

* **Random String Generator** - Generates random string of `n` lenght based on these characters `abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_`
* **Files Upload** - Uploads files and generate random filenames using `Random string Generator` , it also support file size limits and file types customization

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