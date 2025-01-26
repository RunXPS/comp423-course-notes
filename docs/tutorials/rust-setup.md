# Setting up a dev container for Rust

* Primary author: [Ryan Krasinski](https://github.com/RunXPS)
* Reviewer: [Ryan Jacob](https://github.com/rjacob6051)



### Creating the Rust Devcontainer

*Prerequisites: The* **Dev Container** *extension is installed (from the MkDocs Tutorial)*

To start using rust, we must first create a devcontainer to install our dependencies. 

Create a new directory called `rust-dev-container` and initialize it as a git repository with the `git init` command. Within this new directory, create a `.devcontainer` subdirectory and a `devcontainer.json` file, similar to the one created in the MkDocs Tutorial.
In that new file, copy the following code. 
The **name** is up to the developer, however the **image** has been copied from [microsoft's saved images](https://hub.docker.com/r/microsoft/vscode-devcontainers) and the extension is the [rust-analyzer](https://marketplace.visualstudio.com/items?itemName=rust-lang.rust-analyzer) extension for VS Code.

```
  {
    "name": "Rust Image",
    "image": "mcr.microsoft.com/devcontainers/rust:latest",
    "customizations": {
      "vscode": {
        "settings": {},
        "extensions": ["rust-lang.rust-analyzer"]
      }
    }
  }
```
Afterwards, open the `tutorials` directory in a window of VS Code and when prompted, reopen the space in a devcontainer. 

!!! tip ""
    (Use Ctrl + Shift + p and type "Reopen in container" if not prompted to reopen in a container)

Use the `rustc --version` in the terminal to check if the container has been created correctly. The output should be as follows:
```
$ rustc --version
rustc 1.83.0 (########## YYYY-MM-DD)
```

??? question "What if ```rustc --version``` is not recognized?"
    If ```rustc --version``` does not return the version listed above, refollow the devcontainer steps and ensure you are working in the container.

### Creating a New Rust Project

Begin with the `cargo new first-proj --vcs none` command to create the project. Dissecting this command by each term.

 - `cargo` ~ the rust package manager. Used to install dependencies and create, run, build, test, and format programs.
 - `new first-proj` ~ creates a new rust project named "first-proj". The name can change depending on what project the developer intends to create.
 - `--vcs none` ~ defines the **v**ersion **c**ontrol **s**ystem that the project is going to use. In this case, the project won't be created with a version control system

??? question "Why use ```none```?"
    This flag will prevent the initialization of a git repository, which is useful if you have handled version control elsewhere or don't need it.
   
After running the command, there should be a new directory named `first-proj` (or whatever you named the directory) in the workspace. Within, there is are 2 files: `Cargo.toml` and `src/main.rs` (or the `main.rs` file in the `src`) directory. The first defines what iteration of the project you are working on, denoting the project name, version, and edition (which is the year of the Rust release being used), along with the installed project dependencies.    
   
   
In the `main.rs` file, a simple "Hello World" program is prewritten. Enter the new project directory in the terminal using `./first-proj/` command. Then compile the program with `cargo build`. A new file and directory will be created with the packages used during the file's compilation. This is similar to the `gcc -o file.c` command which compiles a C file, which creates an executable object file after compilation. The executable object file created with the previous rust command is not in the current working directory, but within the `debug` subdirectory in the `target` directory. Instead of finding it in the terminal, use the command: `./target/debug/first-proj` (or replace "first-proj" with whatever the project name is).   
   
However, rather than simply running the file with the path, it is sometimes easier to use the `cargo run`, which automatically finds and runs the command. However, this command will automatically compile and run the program. This is large distinction between the "build" and "run" commands, as "run" will always recompile, even if the program has no changes. However, the "build" command will only compile. Running the program from its executable will reduce the extra time after running the command re-compiling.   
   
   
### Putting It All Together
To finish out, let's use all of these concepts to create another program. However, instead of printing "Hello World", it is going to welcome the COMP423 class with "Hello COMP423". Use your knowledge and the previous notes to try these steps on your own. Here's the step by step solution:

1) Initialize the project with a new name and no version control system (make sure you're in the right directory!)
2) Find the rust file and rewrite the function to print "Hello COMP423"   
3) Build and run the program. (There are 2 ways to do this)   
   
Now you are a real rust programmer. Next step, manipulating memory!