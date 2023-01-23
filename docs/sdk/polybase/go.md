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

## Create Record

To create a new entry in the Polybase collection, you need to use the `Create()` method of the collection instance. If your request is successfully executed, you can get the final state of the record in the database, to learn more visit the [Response](go.md#response) paragraph.

**An example of creating a new record in the collection:**

```go
ctx := context.Background()
// Arguments to the collection constructor function.
args := []any{1, "string", true}

coll.Create(ctx, args, nil)
```

{% hint style="info" %}
For the convenience of passing arguments, we added the **ParseInput** function.
{% endhint %}

## Response

There are two response types in go-polybase, `SingleResponse` and `Response`.

`SingleResponse` type is used for requests that return a single record, such requests include all those that call collection functions (constructor, etc.) or receive the specified record by its id.

**An example of a single response:**

```go
type Todo struct {
    ID     int    `json:"id"`
    Title  string `json:"title"`
    Status bool   `json:"status"`
}

var response polybase.SingleResponse[Todo]
```

`Response` type is used for requests that can return more than one record, it includes all requests that are created through filters (limit, before, etc.) or requests that receive all records of the collection.

**An example of a response with possible multiple records:**

```go
var response polybase.Response[Todo]
```

To decode the response returned by the database, you need to pass a pointer to a variable with type response to a method that accepts an argument named `resp`.

**An example of response decoding:**

```go
var response polybase.Response[Todo]

coll.Get(ctx, &response)
```
