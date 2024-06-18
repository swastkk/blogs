---
title: File Server in GO-Language
author: swastik
date: 2023-06-28 09:55:00 +0800
categories: [servefiles, go, fileserver]
tags: [go]
image:
  path: /assets/images/fileserver-main.jpg
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt:
---

**File Server** is a computer attached to a network that provides a location for shared disk access, i.e storage of computer files such as text, image, sound, video that can be accessed by the workstations that are able to reach the computer that shares the access through a computer network.

## Prerequisites

Before we begin , please set up GO environment on your machine. Head over to their [official page](https://go.dev/doc/install) to install if you have not done so.

## Getting Started

Initialise a directory for this `file-server` project and create a go file named `main.go` or `server.go`
and start with importing the pacakages from the main as

```go
import (
  "fmt"
  "net/http"
)
```

The packages used here

- _[fmt](https://pkg.go.dev/fmt)_ -
  Package fmt implements formatted I/O with functions analogous to C's printf and scanf. The format 'verbs' are derived from C's but are simpler.
- _[http](https://pkg.go.dev/net/http)_ - Package http provides HTTP client and server implementations.

Create the main function and use the function `func http.ListenAndServe(addr string, handler http.Handler) error` .

`ListenAndServe` listens on the TCP network address `addr` and then calls Serve with `handler` to handle requests on incoming connections. Accepted connections are configured to enable TCP keep-alives.

```go
http.ListenAndServe(":5000", nil)
```

Check your server is running or not with following commands

```go
go mod init `module_name`
go run `go_file`
```

Now open up the web browser and check `localhost:5000` is running and showing nothing.
![404pagenotfound-image](/assets/images/404-fileserver.png)

Now create a directory inside the go project directory like I have named it as `public` which will contain the files which we will serve over server.

```console
├── go.mod
├── public
│   ├── about.js
│   ├── cv.pdf
│   ├── diagram.fig
│   ├── form.html
│   ├── gatsby-browser.js
│   ├── gatsby-ssr.js
│   ├── Go in 100 Seconds [446E-r0rXHI].mkv
│   └── iste-orange.png
└── server.go
```

Declare the `dir` variable like this

```go
dir := http.Dir("./public/")
```

which will use the `http.Dir()` that implements FileSystem using the native file system restricted to a specific directory tree.

Also An empty Dir is treated as "." and we have used "./public".

Create a variable named `dirHandler` which will use the `FileServer` function and takes the above declared `dir` as input.

```go
dirHandler:= http.FileServer(dir)
```

Lastly call the function `http.Handle()` which will register the handler for the given pattern in the DefaultServeMux.

```go
http.Handle("/", dirHandler)
```

So this was it, now you can add more lines to your code for making it easy to understand

```go
fmt.Printf("FileServer is up and running at port 5000....\n")
```

Run the server with `go run .` and open up the web browser, you will see the fileserver is running
![fileserver-running-image](/assets/images/fileserver-running.png)

Tadda!, we have succesfully made the File Server and test if the files are opening up or not.
![gif](/assets/gifs/test.gif)

## How to send files locally

To set up a sort of quick NAS (Network Attached Storage) system:

1. Make sure both devices are connected through same network via LAN or WiFi.
2. Go to the your `fileserver` directory using `cd` on Linux or MacOS systems or CD for Windows.
3. Start your File server with `go run .`
4. Open new terminal and type `ifconfig` on nix or MacOS or `ipconfig` on Windows and `ip address` on Linux to find your IP address.

Now on the **second device**:

Open browser and type in the IP address of the first machine, along with port 5000

`http://[ip address]:5000`

A page will open showing all the files in the directory being shared from the first computer.

If facing any issue, can refer to the example fileserver at [example](https://github.com/swastkk/go_microservices/tree/master/fileserver).

Happy Hacking :")

<div style="text-align: center;">
  <p style="margin-bottom: 1px;">Visitor Count</p>
  <img src="https://profile-counter.glitch.me/swastkk-file-server-go/count.svg" alt="visitor count" />
</div>