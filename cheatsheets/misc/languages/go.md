# GO Lang Cheatsheet

## Hello World

File `hello.go`:
```go
package main

import "fmt"

func main() {
    fmt.Println("Hello Go")
}
```

`$ go run hello.go`

## Declarations

Type declerations such as vars, constants .. etc.
```go
var foo int // declaration without initialization

var foo int = 42 // declaration with initialization

var foo, bar int = 42, 1302 // declare and init multiple vars at once

var foo = 42 // type omitted, will be inferred

foo := 42 // shorthand, only in func bodies, omit var keyword, type is always implicit

const constant = "This is a constant"
```

## Functions

Here is a normal func definition in go
```
func function_name( [parameter list] ) [return_types] {
   body of the function
}
```

```go
// a simple function
func functionName() {}

// function with parameters (again, types go after identifiers)
func functionName(param1 string, param2 int) {}

// multiple parameters of the same type
func functionName(param1, param2 int) {}

// return type declaration
func functionName() int {
    return 42
}

// Can return multiple values at once
func returnMulti() (int, string) {
    return 42, "foobar"
}
var x, str = returnMulti()

// Return multiple named results simply by return
func returnMulti2() (n int, s string) {
    n = 42
    s = "foobar"
    // n and s will be returned
    return
}
var x, str = returnMulti2()
```

## Built-in Types

```
bool

string

int  int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr

byte // alias for uint8

rune // alias for int32 ~= a character (Unicode code point) - very Viking

float32 float64

complex64 complex12
```

## Type Conversions

```go
var i int = 42
var f float64 = float64(i)
var u uint = uint(f)

// alternative syntax
i := 42
f := float64(i)
u := uint(f)
```

## Packages

- Package declaration at top of every source file
- Executables are in package `main`
- Convention: package name == last name of import path (import path math/rand => package rand)
- Upper case identifier: exported (visible from other packages)
- Lower case identifier: private (not visible from other packages)

## Control structures

### If ... Else
```go
func main() {
	// Basic one
	if x > 10 {
		return x
	} else if x == 10 {
		return 10
	} else {
		return -x
	}

	// You can put one statement before the condition
	if a := b + c; a < 42 {
		return a
	} else {
		return a - 42
	}
}
```

### Loops

```go
    // There's only `for`, no `while`, no `until`
    for i := 1; i < 10; i++ {
    }
    for ; i < 10;  { // while - loop
    }
    for i < 10  { // you can omit semicolons if there is only a condition
    }
    for { // you can omit the condition ~ while (true)
    }
    
    // use break/continue on current loop
```

## Arrays, Slices, Ranges

### Arrays

```go
var a [10]int // declare an int array with length 10. Array length is part of the type!
a[3] = 42     // set elements
i := a[3]     // read elements

// declare and initialize
var a = [2]int{1, 2}
a := [2]int{1, 2} //shorthand
a := [...]int{1, 2} // elipsis -> Compiler figures out array length
```

### Slices

```go
var a []int                              // declare a slice - similar to an array, but length is unspecified
var a = []int {1, 2, 3, 4}               // declare and initialize a slice (backed by the array given implicitly)
a := []int{1, 2, 3, 4}                   // shorthand
chars := []string{0:"a", 2:"c", 1: "b"}  // ["a", "b", "c"]

var b = a[lo:hi]	// creates a slice (view of the array) from index lo to hi-1
var b = a[1:4]		// slice from index 1 to 3
var b = a[:3]		// missing low index implies 0
var b = a[3:]		// missing high index implies len(a)
a =  append(a,17,3)	// append items to slice a
c := append(a,b...)	// concatenate slices a and b
```

### Operations on Arrays and Slices

```go
// loop over an array/a slice
for i, e := range a {
    // i is the index, e the element
}
```

## Maps

```go
m := make(map[string]int)
m["key"] = 42
fmt.Println(m["key"])

delete(m, "key")

elem, ok := m["key"] // test if key "key" is present and retrieve it, if so

// map literal
var m = map[string]Vertex{
    "Bell Labs": {40.68433, -74.39967},
    "Google":    {37.42202, -122.08408},
}

// iterate over map content
for key, value := range m {
}
```

## Structs

There are no classes, only structs. Structs can have methods.

```go
// A struct is mostly a basic class. It creates a data structure with different
// fields that can hold data about a single node

// you create a struct with `type` and `struct` keywords
type Books struct {
   title string
   author string
   subject string
   book_id int
}

func main() {
   var Book1 Books    /* Declare Book1 of type Book */
   var Book2 Books    /* Declare Book2 of type Book */
 
   /* book 1 specification */
   Book1.title = "Go Programming"
   Book1.author = "Mahesh Kumar"
   Book1.subject = "Go Programming Tutorial"
   Book1.book_id = 6495407

   /* book 2 specification */
   Book2.title = "Telecom Billing"
   Book2.author = "Zara Ali"
   Book2.subject = "Telecom Billing Tutorial"
   Book2.book_id = 6495700
 
   /* print Book1 info */
   printBook(Book1)

   /* print Book2 info */
   printBook(Book2)
}

// there is no direct way to write functions inside a struct
// so we pass it as a argument to other functions
func printBook( book Books ) {
   fmt.Printf( "Book title : %s\n", book.title);
   fmt.Printf( "Book author : %s\n", book.author);
   fmt.Printf( "Book subject : %s\n", book.subject);
   fmt.Printf( "Book book_id : %d\n", book.book_id);
}

```

## Pointers

```go
p := Vertex{1, 2}  // p is a Vertex
q := &p            // q is a pointer to a Vertex
r := &Vertex{1, 2} // r is also a pointer to a Vertex

// The type of a pointer to a Vertex is *Vertex

var s *Vertex = new(Vertex) // new creates a pointer to a new struct instance
```

## Interfaces

Go programming provides another data type called interfaces which represents a set of method signatures. The struct data type implements these interfaces to have method definitions for the method signature of the interfaces.

```go
package main

import ("fmt" "math")

/* define an interface */
type Shape interface {
   area() float64
}

/* define a circle */
type Circle struct {
   x,y,radius float64
}

/* define a rectangle */
type Rectangle struct {
   width, height float64
}

/* define a method for circle (implementation of Shape.area())*/
func(circle Circle) area() float64 {
   return math.Pi * circle.radius * circle.radius
}

/* define a method for rectangle (implementation of Shape.area())*/
func(rect Rectangle) area() float64 {
   return rect.width * rect.height
}

/* define a method for shape */
func getArea(shape Shape) float64 {
   return shape.area()
}

func main() {
   circle := Circle{x:0,y:0,radius:5}
   rectangle := Rectangle {width:10, height:5}
   
   fmt.Printf("Circle area: %f\n",getArea(circle))
   fmt.Printf("Rectangle area: %f\n",getArea(rectangle))
}
```

## Exception Handling

There is no exception handling. Instead, functions that might produce an error just declare an additional return value of type error. This is the error interface:

```go
// The error built-in interface type is the conventional interface for representing an error condition,
// with the nil value representing no error.
type error interface {
    Error() string
}
```
Here is an example:
```go

func sqrt(x float64) (float64, error) {
	if x < 0 {
		return 0, errors.New("negative value")
	}
	return math.Sqrt(x), nil
}

```

## Modules and Packages

A go `package` is a collection of .go files in a directory and using packages you can orginize your code neatly. Go `modules` are basically pacakges with dependincies and versioning like pip pacakges in python.

Before diving into go modules, know that go sets its configuration in envioroment variables. You can access them with this command:
```
$ go env
```
In particular, three Go environment variables are worth mentioning
- GOROOT — specifies where your GO SDK is located.
- GOPATH — specifies the root of your workspace (where your packages and dependencies are located).
- GO111MODULE — specifies how Go imports your packages. It can assume the following three values: “on”, “off”, or “auto”.

A module is a directory of packages with a file named `go.mod` at its root. The go.mod file defines the module’s import path, as well as its specific dependencies


### GO111MODULE=on

If the GO111MODULE=on is "on" you can use this for local packages:
```
HelloApp
   |___main.go
   |___geometry
       |___geometry.go
```
geometry.go:
```go
package geometry
import (
    "math"
)
type Point struct {
    X float64
    Y float64
}
func (p Point) Length() float64 {
    return math.Sqrt(math.Pow(p.X, 2.0) + math.Pow(p.Y, 2.0))
}
```
main.go:
```go
package main
import (
    "fmt"
    "myapp/geometry"
)
func main() {
    pt1 := geometry.Point{X: 2, Y: 3}
    fmt.Println(pt1)
    fmt.Println(pt1.Length())
}
```

For third party pacakage improts, read this, I am too lazy to do it right now: https://levelup.gitconnected.com/using-modules-and-packages-in-go-36a418960556



## Folder Strucrure

- `cmd/` -- Main applications for this project. The directory name for each application should match the name of the executable you want to have (e.g., /cmd/myapp ) If you think the code can be imported and used in other projects, then it should live in the /pkg directory. If the code is not reusable or if you don't want others to reuse it, put that code in the /internal directory. It's common to have a small main function that imports and invokes the code from the /internal and /pkg directories and nothing else.
- `internal/` -- Private application and library code. This is the code you don't want others importing in their applications or libraries. Note that this layout pattern is enforced by the Go compiler itself. You can optionally add a bit of extra structure to your internal packages to separate your shared and non-shared internal code. It's not required 
- `pkg/` -- Library code that's ok to use by external applications (e.g., /pkg/mypubliclib). Other projects will import these libraries expecting them to work, so think twice before you put something here :-) Note that the internal directory is a better way to ensure your private packages are not importable because it's enforced by Go.
- `vendor/` -- Application dependencies (managed manually or by your favorite dependency management tool like the new built-in Go Modules feature). The go mod vendor command will create the /vendor directory for you. Don't commit your application dependencies if you are building a library.
- `api/` -- OpenAPI/Swagger specs, JSON schema files, protocol definition files.
- `web/` -- Web application specific components: static web assets, server side templates and SPAs.
- `configs/` -- Configuration file templates or default configs.
- `init/` -- System init (systemd, upstart, sysv) and process manager/supervisor (runit, supervisord) configs
- `scripts/` -- Scripts to perform various build, install, analysis, etc operations.
- `build/` -- Packaging and Continuous Integration. Put your cloud (AMI), container (Docker), OS (deb, rpm, pkg) package configurations and scripts in the /build/package directory.
- `deployments/` -- IaaS, PaaS, system and container orchestration deployment configurations and templates (docker-compose, kubernetes/helm, mesos, terraform, bosh).
- `tests/` -- Additional external test apps and test data. Feel free to structure the /test directory anyway you want. For bigger projects it makes sense to have a data subdirectory
- `docs/` -- Design and user documents (in addition to your godoc generated documentation).
- `tools/` -- Supporting tools for this project. Note that these tools can import code from the /pkg and /internal directories.
- `examples/` -- Examples for your applications and/or public libraries.
- `third_party/` -- External helper tools, forked code and other 3rd party utilities (e.g., Swagger UI).
- `githooks/` -- Git hooks.
- `assets/` -- Other assets to go along with your repository (images, logos, etc).
- `website` -- This is the place to put your project's website data if you are not using GitHub pages.


## References

- https://github.com/a8m/golang-cheat-sheet