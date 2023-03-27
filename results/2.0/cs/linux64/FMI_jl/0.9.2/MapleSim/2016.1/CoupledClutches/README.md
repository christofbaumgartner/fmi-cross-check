# FMI.jl

## How can I use FMI.jl?
1\. Open a Julia-REPL, switch to package mode using `]`, activate your preferred environment.


2\. Install [*FMI.jl*](https://github.com/ThummeTo/FMI.jl):

```julia-repl
(@v1.6) pkg> add FMI
```

3\. If you want to check that everything works correctly, you can run the tests bundled with [*FMI.jl*](https://github.com/ThummeTo/FMI.jl):

```julia-repl
(@v1.6) pkg> test FMI
```

4\. Have a look inside the [examples folder](https://github.com/ThummeTo/FMI.jl/tree/examples/examples) in the examples branch or the [examples section](https://thummeto.github.io/FMI.jl/dev/examples/overview/) of the documentation. All examples are available as Julia-Script (*.jl*), Jupyter-Notebook (*.ipynb*) and Markdown (*.md*).

## How can I simulate a FMU and plot values?
```julia
using FMI, Plots

# load and instantiate a FMU
myFMU = fmiLoad(pathToFMU)

# simulate from t=0.0s until t=10.0s and record the FMU variable named 'mass.s'
simData = fmiSimulate(myFMU, 0.0, 10.0; recordValues=['mass.s'])

# plot it!
fmiPlot(simData)

# free memory
fmiUnload(myFMU)
```