Go localinstall
===============

Sometimes you need to run local install for development.

But Go don't let you run something `go install .`, it would complain you about:

    go install: no install location for ...

So that you need to put your repository into the $GOPATH structure manually to 
make a install locally.

For most people there are some solutions:

1. create src/, pgk/, bin/ structure in the repository, then add current
   directory to $GOPATH.
2. copy or link repository path to $GOPATH by commands.

To the first solution, most packages are not in this kind of structure.

To the second solution, copying or linking paths are tiresome.

## go-localinstall

To let something like this work:

	import "github.com/c9s/gorepo/lib"
	import "reallycool"

we need to link current directory to GOPATH

	ln -s $GOPATH/src/github.com/c9s/gorepo .
	ln -s $GOPATH/src/reallycool .

local-install stragegy:

1. find local install config file
2. Get import path from repository path (git, hg ... etc), or package name.
3. use GOPATH to link package repository
4. run build

