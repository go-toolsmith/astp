[![Go Report Card](https://goreportcard.com/badge/github.com/go-toolsmith/astp)](https://goreportcard.com/report/github.com/go-toolsmith/astp)
[![GoDoc](https://godoc.org/github.com/go-toolsmith/astp?status.svg)](https://godoc.org/github.com/go-toolsmith/astp)
[![Build Status](https://travis-ci.org/go-toolsmith/astp.svg?branch=master)](https://travis-ci.org/go-toolsmith/astp)


# astp

Package astp provides AST predicates.

## Installation:

```bash
go get github.com/go-toolsmith/astp
```

## Example

```go
import "github.com/go-toolsmith/astp"

func Walk(var node ast.Node) {
    switch {
    case astp.IsValueSpec(node):
        value := node.(*ast.ValueSpec)

        for _, name := range value.Names {
            if name != nil {
                println("value name: " + name.Name)
            }
        }

    case astp.IsFuncDecl(node):
        fn := node.(*ast.FuncDecl)
        if fn.Name != nil {
            println("function: " + fn.Name.Name)
        }
    }
}
```