# containers-with-go
Building containers from scratch with golang

For building a container from scratch we have to understand what happens when you run `docker run <image>`


Open terminal and run:
`docker run --rm -it ubuntu /bin/bash`

#hostname → shows the hostname

#ps → shows the processes running with PID

#exit


## Namespaces:
A namespace is where we limit what a process can see, we setup these namespaces using syscalls, it potentially restricting the view that the process has on the host machine


## Chroot

## Cgroups

