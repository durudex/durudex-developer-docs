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

To start using the Polybase client, you need to create a new client instance and configure it.

**An example of creating a new client instance:**

```go
import "github.com/durudex/go-polybase"

func main() {
    client := polybase.New(polybase.Config{
        // You can use your own URL.
        URL: polybase.TestnetURL,
    })
}
```

## Collection

To use Polybase collections, you need to create instances of the collections you need. To create instances, you need to use the `Collection()` client method, passing the full name of the collection, which consists of the namespace and the collection name separated by a slash.

**An example of creating a new collection instance:**

```go
coll := client.Collection("Namespace/Collection")
```

{% hint style="info" %}
If you specify the **DefaultNamespace** in the client configuration, you won't need to specify it every time you create a new instance.
{% endhint %}

