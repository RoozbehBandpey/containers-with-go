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
`# go run main.go run echo hello world`

Tou can also run shell

`$ go run main.go run echo bin/bash`

`$ ps`
You should see shell as background process

Now we want to containerize this command by creating some namespaces, by specifying
```go
cmd.SysProcAttr = &syscall.SysProcAttr
```
and providing `Cloneflags` because cloning is what creates new process that we are going to run an arbitrary command in. We will start with Unix time Sharing system.

### Unix time Sharing system
It basically makes the namespace, the hostname. It will let us to have our own hostname inside the container.

Now if you run the command 
`$ go run main.go run echo bin/bash`

and 

`$ hostname`

You'll see it has inherited the hostname from your host machine, but you can now change the hostname by just typing `hostname <new hotname>`


NOTE:
If you are using vscode on mac add the following in `setting.json`

```json
"go.toolsEnvVars": {"GOOS" : "linux"},
```
cmd+shift+p

Type `setting.json`

## Chroot

## Cgroups

