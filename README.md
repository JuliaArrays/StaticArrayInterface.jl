# StaticArrayInterface.jl

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://juliaarrays.github.io/StaticArrayInterface.jl/stable)
[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://juliaarrays.github.io/StaticArrayInterface.jl/dev)
[![CI](https://github.com/JuliaArrays/StaticArrayInterface.jl/workflows/CI/badge.svg)](https://github.com/JuliaArrays/StaticArrayInterface.jl/actions?query=workflow%3ACI)
[![Build status](https://badge.buildkite.com/a2db252d92478e1d7196ee7454004efdfb6ab59496cbac91a2.svg?branch=master)](https://buildkite.com/julialang/StaticArrayInterface-dot-jl)
[![codecov](https://codecov.io/gh/JuliaArrays/StaticArrayInterface.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/JuliaArrays/StaticArrayInterface.jl)

The AbstractArray interface in Base Julia does not always enforce static guarantees.
For example, if the size of an array is known at compile time, many of the indexing
schemes are not specialized to make use of that size to build fully optimized code.
In most cases a user should rely on the compiler to deduce the static properties
and perform the optimization. However, some brave souls believe they can beat the
compiler, and this library is for them. 

Functions like `known_length` return values using [Static.jl](https://github.com/SciML/Static.jl)
which encode all of the information at the type level, which in turn forces the
computation to occur at compile time.

## Warning: Compile Times

Because this library enforces things be done at compile time by encoding everything
into types, using it will increase your compile times. You have been warned, now
proceed (with caution).
