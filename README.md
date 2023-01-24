# Golang toolkit

A simple go module that provides commonly used go-tools 

## Features

* **Random String Generator** - Generates random string of `n` lenght based on these characters `abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_`
* **Files Upload** - Upload files and generate random filenames using `Random string Generator` , it also support file size limits and file types customization
* **Creating Directory** - Create directories it they don't exist
* **Generating Slugs** - Generate slugs from a string
* **Downloading Static Files** - Download files and forces browser not to display such files
* **Working with JSON** - provides quick way to read & write JSON

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

#### Slugifying a string

```go
package main

import (
	"log"

	"github.com/barcollin/toolkit"
)

func main() {
	toSlug := "NOW!!! is the time 123"

	var tools toolkit.Tools

	slugified, err := tools.Slugify(toSlug)
	if err != nil {
		log.Println(err)
	}

	log.Println(slugified)

}


```

#### Working with JSON

```go
package main

import (
	"log"
	"net/http"

	"github.com/barcollin/toolkit"
)

func main() {
	// get routes
	mux := routes()

	// start a server
	err := http.ListenAndServe(":8080", mux)
	if err != nil {
		log.Fatal(err)
	}

}

func routes() http.Handler {
	mux := http.NewServeMux()

	mux.Handle("/", http.StripPrefix("/", http.FileServer(http.Dir("."))))
	mux.HandleFunc("/download", downloadFile)

	return mux

}

func downloadFile(w http.ResponseWriter, r *http.Request) {
	t := toolkit.Tools{}
	t.DownloadStaticFile(w, r, "./files", "img.png", "puppy.png")
}

```