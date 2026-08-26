# ghūl scratchpad

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/degory/ghul-scratchpad?quickstart=1)

A one-file [ghūl](https://ghul.dev) project for trying the language out. Open it in a GitHub Codespace and you get an editor with the compiler, the runtime and the ghūl language extension already installed, so an example from the website runs as soon as you paste it in.

## in a GitHub Codespace

Click the badge above. The container installs the compiler and builds the project as it starts, which takes a minute or two the first time.

## on your own machine

You need the [.NET 10 SDK](https://dotnet.microsoft.com/download/dotnet/10.0), and [Visual Studio Code](https://code.visualstudio.com/) with the [ghūl extension](https://marketplace.visualstudio.com/items?itemName=degory.ghul) for error highlighting, hover and completion:

```sh
git clone https://github.com/degory/ghul-scratchpad.git
cd ghul-scratchpad
dotnet tool restore
```

The repository also carries a dev container definition, so opening the folder in Visual Studio Code and reopening in a container works too.

## running it

```sh
dotnet run
```

In Visual Studio Code, the `run` task is the default test task, so <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> then `Tasks: Run Test Task` runs it without leaving the editor.

## pasting an example

`main.ghul` holds the whole program. Replace its contents with any example from [ghul.dev](https://ghul.dev) and run it again.

A file with no `namespace` declaration can carry statements at the top level, which is what `main.ghul` does, so short programs need no `entry()` function. Examples written the other way, with their code inside an `entry()` function, run the same way.

Two things to know when an example doesn't run as pasted:

- A snippet that only declares things has nothing to run, and the compiler reports `no entry point declared`. Add a call at the bottom of the file.
- A few of the website's examples show code that is meant to fail, and a few need a package the scratchpad does not reference. For those, `dotnet add package <name>` pulls the package in.

To spread a program over several files, add them next to `main.ghul` and give each one the same `namespace`; the project compiles every `.ghul` file under its directory.

## what's here

| | |
| --- | --- |
| `main.ghul` | the program |
| `scratchpad.ghulproj` | the project: .NET 10 executable, referencing `ghul.runtime` |
| `.config/dotnet-tools.json` | pins the `ghul.compiler` tool version |
| `ghul.json` | tells the language extension to keep the compiler tool up to date |
| `.devcontainer/` | the Codespace and dev container definition |
| `.vscode/` | build and run tasks, and the extension recommendation |

## issues

[View open issues](https://github.com/degory/ghul/issues?q=is%3Aopen+is%3Aissue+label%3Aghul-scratchpad) or [raise a new one](https://github.com/degory/ghul/issues/new?labels=ghul-scratchpad).
