# Blackfriday-Confluence
Blackfriday-Confluence is confluence wiki renderer for the [Blackfriday v2](https://github.com/russross/blackfriday) markdown processor.

## Features
* :pencil2:Confluence wiki output
* :angel:Support for some of the [Confluence Wiki Markup](https://confluence.atlassian.com/confcloud/confluence-wiki-markup-938044804.html)

## Installation
```
$ go get -u github.com/kentaro-m/blackfriday-confluence
```

## Usage
```go
import (
  bf "gopkg.in/russross/blackfriday.v2"
  bfconfluence "github.com/kentaro-m/blackfriday-confluence"
)

// ...
renderer := &bfconfluence.Renderer{}
extensions := bf.CommonExtensions
md := bf.New(bf.WithRenderer(renderer), bf.WithExtensions(extensions))
input := "# sample text" // # sample text
ast := md.Parse([]byte(input))
output := renderer.Render(ast) // h1. sample text
fmt.Printf("%s\n", output)
// ...
```

## Examples

### Input
```
# Section
Some _Markdown_ text.

## Subsection
Foobar.

### Subsubsection
Fuga

> quote

- - - -

**strong text**
~~strikethrough text~~
[Example Domain](http://www.example.com/)
![](https://blog.golang.org/gopher/header.jpg)

* list1
* list2
* list3

hoge

1. number1
2. number2
3. number3

First Header  | Second Header
------------- | -------------
Content Cell  | Content Cell
Content Cell  | Content Cell

|a  |b  |c  |
|---|---|---|
|1  |2  |3  |
|4  |5  |6  |
```

### Output
```
h1. Section
Some _Markdown_ text.

h2. Subsection
Foobar.

h3. Subsubsection
Fuga

{quote}quote

{quote}

----
*strong text*
-strikethrough text-
[http://www.example.com/|Example Domain]
!https://blog.golang.org/gopher/header.jpg!

* list1
* list2
* list3

hoge

# number1
# number2
# number3

||First Header||Second Header||
|Content Cell|Content Cell|
|Content Cell|Content Cell|

||a||b||c||
|1|2|3|
|4|5|6|
```

## Documentation

## Todo
- [ ] CI Support (testing, publish the package)
- [ ] Publish the GoDoc

## Contributing

### Issue

* :bug: Report a bug
* :gift: Request a feature

Please use the [GitHub Issue](https://github.com/kentaro-m/blackfriday-confluence/issues) to create a issue.

### Pull Request

1. Fork it (<https://github.com/kentaro-m/blackfriday-confluence/fork>)
2. Create your feature branch
3. Run the test (`$ go test`) and make sure it passed :white_check_mark:
4. Commit your changes :pencil:
5. Push to the branch
6. Create a new Pull Request :heart:

## Thanks
Blackfriday-Confluence is inspired by [Blackfriday-LaTeX](https://github.com/Ambrevar/blackfriday-latex).

## License
MIT
