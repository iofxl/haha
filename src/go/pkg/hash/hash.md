# [Package hash](https://golang.org/pkg/hash/)

# Overview

Package hash provides interfaces for hash functions. 

各种Hash方法怎么朆在这个包里，而在crypto包里

# type Hash, Hash32, Hash64 interface

```go
type Hash interface {
        // Write (via the embedded io.Writer interface) adds more data to the running hash.
        // It never returns an error.
        io.Writer

        // Sum appends the current hash to b and returns the resulting slice.
        // It does not change the underlying hash state.
        Sum(b []byte) []byte

        // Reset resets the Hash to its initial state.
        Reset()

        // Size returns the number of bytes Sum will return.
        Size() int

        // BlockSize returns the hash's underlying block size.
        // The Write method must be able to accept any amount
        // of data, but it may operate more efficiently if all writes
        // are a multiple of the block size.
        BlockSize() int
}

type Hash32 interface {
        Hash
        Sum32() uint32
}

type Hash64 interface {
        Hash
        Sum64() uint64
}
```
