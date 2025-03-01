#languages 
### Gotcha in Slices and Arrays

As mentioned earlier, re-slicing a slice doesn’t make a copy of the underlying array. The full array will be kept in memory until it is no longer referenced. Occasionally this can cause the program to hold all the data in memory when only a small piece of it is needed. [Ref](https://go.dev/blog/slices-intro#a-possible-gotcha) for more reading.

### Tests

### Test organisation

Suppose, we want to write test for `foo.go` having `foo` package name and interfaces `FooInterface` and `BarInterface`. We create foo_test.go in the same directory with package name `foo_test`. For generated mocks, we can create a directory mocks and place them there.
#### Running test

Tests can be run with:

```shell
go test docode/do/src/teams/compute/docr/
```

To run specific test
```shell
go test docode/do/src/teams/compute/docr/ -run TestAuditRegistry
```

### Generating Mocks for test

We can use [gomock](https://github.com/uber-go/mock) to generate mocks for golang interfaces. It can be generated in below ways:

1. Using package mode
```shell
mockgen -package mocks -destination ./mocks/foo_test.go foo FooInterface,BarInterface
```

2. Using source mode
```shell
mockgen -package mocks -destination ./mocks/foo_test.go -source=foo.go FooInterface,BarInterface
```

To automate it, we can add below comment in foo.go:
```go
//go:generate mockgen -package mocks -destination ./mocks/foo_test.go foo FooInterface,BarInterface
```

and run `go generate ./...` to generate the mocks

#### Cycle not allowed in tests

Sometimes, when interface's function returns a custom type like struct, the generated mocks would refer to the type in the tested package and might cause circular imports. If we follow the structure described in [[#Test organisation]], it can be avoided. If you are still facing this issue, it might be good advice to separate the tested package `foo` to its own sub-package.