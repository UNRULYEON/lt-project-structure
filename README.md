# lt-project-structure

A example project explaining good practice for a .NET Core project with React and TypeScript

## Index

- [Project setup](#project-setup)
  - [Generating `global.json`](#generating-globaljson)
  - [Generating .NET Core with React project](#generating-net-core-with-react-project)

## Prerequisites

- [.NET Core](https://dotnet.microsoft.com/download)
- [Node](https://nodejs.org/en/download/)

## Project setup

### Generating `global.json`

It's always a good idea to document and enforce the .NET version that's going to be used. This can be done with the `global.json`.

Check what version are installed:

```zsh
λ dotnet --list-sdks
2.1.802 [/usr/local/share/dotnet/sdk]
2.1.804 [/usr/local/share/dotnet/sdk]
3.0.100 [/usr/local/share/dotnet/sdk]
3.1.201 [/usr/local/share/dotnet/sdk]
```

Generate `global.json`:

```zsh
λ dotnet new globaljson --sdk-version 3.1.201
The template "global.json file" was created successfully.
```

Run the command above in the folder where the project will be created.

[Docs](https://docs.microsoft.com/en-us/dotnet/core/tools/global-json?tabs=netcore3x)

[⬆ Back to index](#index)

---

### Generating .NET Core with React project

There is no template for a React project with TypeScript at this point, so we'll have to convert the project to one.

Generate the .NET Core with React project:

```zsh
λ dotnet new react
The template "ASP.NET Core with React.js" was created successfully.

Processing post-creation actions...
Running 'dotnet restore' on /Users/amarkisoensingh/projects/amar.sh/lt-project-structure/lt-project-structure.csproj...
  Restore completed in 304.99 ms for /Users/amarkisoensingh/projects/amar.sh/lt-project-structure/lt-project-structure.csproj.

Restore succeeded.
```

Run the command above in the folder where the project will be created.

[Docs](https://docs.microsoft.com/en-us/dotnet/core/tools/dotnet-new#examples)

[⬆ Back to index](#index)

---