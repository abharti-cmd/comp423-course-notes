# Setting up a dev container for Go 

* Primary author: [Arya Bharti](https://github.com/abharti-cmd)
* Reviewer: [Hamsini Tankala](https://github.com/htankala)

# Go DevContainer Setup Tutorial

## Prerequisites
Before we dive into this GO Tutorial, make sure you have:

- A GitHub account: If you don’t have one yet, sign up at [GitHub](https://github.com/).
- Git installed: [Install Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) if you don’t already have it.
- Visual Studio Code (VS Code): Download and install it from [here](https://code.visualstudio.com/).
- Docker installed: Required to run the dev container. Get Docker [here](https://www.docker.com/products/docker-desktop).
- Command-line basics: Your command-line knowledge will serve you well here. If you need go back to our previous tutorials in class that over the CLI commands!

# Part 1. Project Setup: Creating the Repository

## Step 1. Create a Local Directory and Initialize Git

**(A)** Open your terminal or command prompt.

**(B)** Create a new directory for your project. *(Note: Of course, if you'd like to organize this tutorial somewhere else on your machine, go ahead and change into that parent directory first. By default, this will be in your user's home directory):*

```bash
mkdir go-tutorial-426
cd  go-tutorial-426
```

**(C)** Initialize a new Git repository:
```bash
git init
```
**(D)** Create a README file:
```bash
echo "# Go Tutorial" > README.md
git add README.md
git commit -m "Initial commit with README"
```

# Part 2: Setting Up the DevContainer
## Step 1. Add Development Container Configuration
**(A)** Create a .devcontainer directory:
```bash
mkdir .devcontainer
touch .devcontainer/devcontainer.json
```
**(B)** Open project in VSCode:
```bash
code . 
```

**(C)** Add the following content to devcontainer.json:
```json
{
  "name": "Go Dev Container",
  "image": "mcr.microsoft.com/vscode/devcontainers/go:latest",
  "customizations": {
    "vscode": {
      "extensions": ["golang.go"]
    }
  },
  "settings": {
    "go.gopath": "/go"
  }
}
```

!!! note "What is a DevContainer?"
    A DevContainer is a development environment defined by configuration files, enabling a consistent and isolated workspace. It uses Docker to manage the container.


##Step 2. Reopen the Project in a VSCode Dev Container
Reopen the project in the container by pressing Ctrl+Shift+P (or Cmd+Shift+P on Mac), typing "Dev Containers: Reopen in Container," and selecting the option. This may take a few minutes while the image is downloaded and the requirements are installed.

Once your dev container setup completes, close the current terminal tab (trash can), open a new terminal pane within VSCode, and try running ``` go version``` to see your dev container is running a recent version of Go without much effort! 

# Part 3: Writing a Basic Go Program
##Step 1. Create the Go File
**(A)** Create a src directory and add a main.go file:
```bash
mkdir src
cd src
touch main.go
```

**(B)** Add the following code to main.go:
```bash
package main

import "fmt"

func main() {
    fmt.Println("Hello COMP423")
}
```

# Part 4: Running and Building the Go Program
## Step 1. Run the Program
**(A)** Verify the Go installation in the container:
```bash
go version
```
**(B)** Initialize a Go module:
```bash
go mod init go-tutorial-426
```
**(C)** Run the program:
```bash
go run main.go 
```
"//go src/run main.go"
!!! example "Expected Output"
    When you run the program, you should see the following output in your terminal:
    ```
    Hello COMP423
    ```
