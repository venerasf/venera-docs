# Installation Process

The installation process tends to be very straight forward since all dependencies are easily managed by golang package manager.

## Installing Golang

From a completely empty machine, let's start with the installation of golang. I will be using a debian machine.

Install the necessary tools.

```
apt update
apt install -y git wget
```

Download the latest version of the language from the official website[^1].

```
wget https://go.dev/dl/go(latest).linux-amd64.tar.gz
tar xvf https://go.dev/dl/go(latest).linux-amd64.tar.gz
mv go/ ~
ln -s ~/go/bin/go /usr/bin/
```

Testing.

```
root@venera:~# go version
go version go1.21.2 linux/amd64
```

## Downloading and compiling Source Code

```
git clone https://github.com/venerasf/Venera.git
cd Venera
```

After the first `go run` execution it will start the installation of all needed dependencies.

```
root@venera:~/Venera# go run venera
go: downloading github.com/c-bata/go-prompt v0.2.6
go: downloading github.com/yuin/gopher-lua v1.0.0
go: downloading github.com/cheynewallace/tabby v1.1.1
go: downloading github.com/mattn/go-sqlite3 v1.14.3
go: downloading gopkg.in/yaml.v2 v2.3.0
...
```

After installing all dependencies the tool will try to run, at this point some errors may occur as the tool will try to configure the default environment.

If you notice some error envolving `go-sqlite3` install build essentials package of your distro.

A folder was created in the user's home (`~/.venera`), where the settings, database, logs and the default location for keeping the scripts are located.

```
root@venera:~/Venera# go run .

        ╦  ╦┌─┐┌┐┌┌─┐┬─┐┌─┐  ╔═╗┬─┐┌─┐┌┬┐┌─┐┬ ┬┌─┐┬─┐┬┌─
        ╚╗╔╝├┤ │││├┤ ├┬┘├─┤  ╠╣ ├┬┘├─┤│││├┤ ││││ │├┬┘├┴┐
         ╚╝ └─┘┘└┘└─┘┴└─┴ ┴  ╚  ┴└─┴ ┴┴ ┴└─┘└┴┘└─┘┴└─┴ ┴
           Recon Mission: github.com/farinap5/venera
           Read https://venera.farinap5.com/
                type 'help'      0.90-NotStable

[vnr]>>
```

Now you can start using Venera.

You may use `dokerfile` as well.

[^1]: https://go.dev/dl/