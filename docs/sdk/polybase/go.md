---
description: Welcome to the Go Polybase client documentation.
---

# Go

## Setup

To get the [`go-polybase`](https://github.com/durudex/go-polybase) module, you need to have or install Go version >= [1.18](https://go.dev/dl/). To check your current version of Go, use the `go version` command.

**The command to get the module:**

```bash
go get github.com/durudex/go-polybase@latest
```

## Client

To start using the Polybase client, you need to create and configure it.

**An example of creating a new client:**

```go
import "github.com/durudex/go-polybase"

func main() {
    client := polybase.New(polybase.Config{
        // You can use your own URL.
        URL: polybase.TestnetURL,
    })
}
```
