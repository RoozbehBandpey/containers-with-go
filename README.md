# containers-with-go
Building containers from scratch with golang

For building a container from scratch we have to understand what happens when you run `docker run <image>`


Let's run an interactive ubuntu-based and shell

Open terminal and type:
`docker run --rm -it ubuntu /bin/bash`

`$ hostname` shows the hostname of container, aa random identity allocated to our container

`$ ps` shows the processes running with their PID

Running same command in host os, you'll see much higher processes running

`$ exit`


## Namespaces:
A namespace is where we limit what a process can see, we setup these namespaces using syscalls, it potentially restricting the view that the process has on the host machine.


[main](main.go) simulates the ability to run an arbitrary command

run 
`go run main.go run echo hello world`
## Chroot

## Cgroups

