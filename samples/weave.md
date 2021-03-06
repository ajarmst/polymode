---
title : Intro to Weave.jl with Gadfly
author : Matti Pastell
date : 13th December 2016
---

This a sample [Julia](http://julialang.org/) markdown document that can
be executed using [Weave.jl](https://github.com/mpastell/Weave.jl).

The code is delimited from docs using markdown fenced code blocks
markup which can be seen looking at the source document
[gadfly_md_sample.jmd](gadfly_md_sample.jmd)
in the examples directory of the package. The source document can be executed
and the results with Gadfly plots are captured in the resulting file.

You can create markdown output or pdf (with xelatex) and HTML directly using
the weave command as follows:

```{lang=julia; eval=false}
using Weave
#Markdown
weave(Pkg.dir("Weave","examples","gadfly_md_sample.jmd"), informat="markdown",
  out_path = :pwd, doctype = "pandoc")
#HTML
weave(Pkg.dir("Weave","examples","gadfly_md_sample.jmd"), informat="markdown",
  out_path = :pwd, doctype = "md2html")
#pdf
weave(Pkg.dir("Weave","examples","gadfly_md_sample.jmd"), informat="markdown",
  out_path = :pwd, doctype = "md2pdf")
```

*The markdown variant used for html and pdf output is Julia markdown.*


The documents will be written to the Julia working directory when you
use the `out_path = :pwd`.

## Capturing code

The basic code chunk will be run with default options and the code and
output will be captured.

```julia
using Gadfly
x = linspace(0, 2*pi)
println(x)
plot(x = x, y = sin(x))
```

You can also control the way the results are captured, plot size etc.
using chunk options. Here is an example of a chunk that behaves like a repl.

```{julia;term=true}
x = 1:10
d = Dict("Weave" => "testing")
y = [2, 4 ,8]
```

You can also for instance hide the code and show only the figure, add a
caption to the figure and make it wider as follows (you can only see the
syntax from the source document):

```{julia;echo=false; fig_cap="A random walk."; label="random"; fig_width=7; fig_height=4}
plot(y = cumsum(randn(1000, 1)), Geom.line)
```

## Whats next

Read the documentation:

  - stable: [http://mpastell.github.io/Weave.jl/stable/](http://mpastell.github.io/Weave.jl/stable/)
  - latest: [http://mpastell.github.io/Weave.jl/latest/](http://mpastell.github.io/Weave.jl/latest/)

See other examples in the [Github repo](https://github.com/mpastell/Weave.jl/tree/master/examples)
