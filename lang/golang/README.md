# Golang container

In this example, we will compile a Go source code in a Singularity container.

<br>


#### What you need:
 - Singularity, which you can download and install from [here](https://github.com/sylabs/singularity).
 - Go source code, (like this [example](https://raw.githubusercontent.com/sylabs/examples/master/lang/golang/hello-world.go)).

<br>



## Setup:

First, make the working directory:

```
$ mkdir golang-container
$ cd golang-container/
```

<br>

Then, pull the container from the library:

```
$ singularity pull golang.sif library://sylabs/examples/golang:latest
```

<br>

Verify the container: (Optional)

```
$ singularity verify golang_latest.sif 
Verifying image: golang_latest.sif
Data integrity checked, authentic and signed by:
        westleyk (examples) <westley@sylabs.io>, KeyID F1E47D55A7F3A56C
```

<br>


## Testing it:

First, we need our source code, you can download this [`hello-world.go`](https://raw.githubusercontent.com/sylabs/examples/master/lang/golang/hello-world.go
):

```
$ wget https://raw.githubusercontent.com/sylabs/examples/master/lang/golang/hello-world.go
```

<br>

Compiling the code:

```
$ ./golang.sif build hello-world.go
# then run the code
$ ./hello-world
hello world!
```

The `golang.sif` is basically the `go` command, running in the container.

<br>

Adding `golang.sif` to `$PATH`:

```
$ export PATH=$PATH:$HOME/golang-container/
```

Now you should have `golang.sif` command.

<br>

## Building the container from a definition file:

You will need root access when building from a definition file.

Here's the [definition file](https://raw.githubusercontent.com/sylabs/examples/master/lang/golang/golang.def), which can be modified as needed.

Then to build the container:

```
$ sudo singularity build golang.sif golang.def
```

<br>

____

<br>


