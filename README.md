# errors-go
This package is a thin wrapper around the Go standard library's errors 
package that provides additional functions for defining and manipulating errors. It is designed to be compatible with 
the standard library's errors package, but also provides additional features such as the ability to define custom error 
codes (for translation or representation in UIs) and the ability to wrap multiple errors in a single error value.

## Features
- Define custom error codes with the `Error` type.
- Wrap multiple errors in a single error value with the `Group` type.
- Retrieve the cause of an error with the `Unwrap` method.

## Getting Started
To get started with the `errors-go` package, you can install it with the following command:

```bash
go get github.com/your-username/errors
```

## Examples 
Here are a few examples, for more examples please consult the `errors_test.go` file.
### Adding context to an error
```go
_, err := os.ReadFile(f)
if err != nil {
	return errors.Wrap(err, "reading_failure", "there was an error reading the file")
}
```



### Handling an error with a specific error code
```go
import "github.com/morebec/errors-go/errors"

func doSomething() error {
	// Return a new error with the "invalid_input" code.
	return errors.New("invalid_input")
	
	// alternatively if you also want to provide a message
	return errors.NewWithMessage("invalid_input", "The input provided was invalid.")
}

func main() {
	err := doSomething()
	if err != nil {
		if errors.HasCode(err, "invalid_input") {
		    // Do something ...
        }
	}
}
```


### Contributions
We welcome contributions to the `errors-go` package! If you have an idea for a new feature or have found a bug, 
please open an issue to discuss it. If you'd like to contribute code, please open a pull request with your changes.

License
The `errors-go` package is licensed under the MIT License.