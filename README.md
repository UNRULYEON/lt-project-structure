# lt-project-structure

A example project explaining good practice for a .NET Core project with React and TypeScript

## Index

- [Project setup](#project-setup)
  - [Generating `global.json`](#generating-globaljson)
  - [Generating .NET Core with React project](#generating-net-core-with-react-project)
- [Converting to TypeScript](#converting-to-typescript)
  - [Upgrading `react-scripts`](#upgrading-react-scripts)
  - [Removing `ESlint` packages](#removing-eslint-packages)
  - [Adding TypeScript](#adding-typescript)

## Prerequisites

- [.NET Core](https://dotnet.microsoft.com/download)
- [Node](https://nodejs.org/en/download/)
- [Yarn](https://yarnpkg.com/getting-started/install)

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

## Converting to TypeScript

### Upgrading `react-scripts`

Go to the `ClientApp` folder, remove `package-lock.json` and install packages:

```zsh
λ cd ClientApp
λ rm package-lock.json
λ yarn

• • •

success Saved lockfile.
✨  Done in 31.93s.
```

Run the following command to check which version `react-scripts` is:

```zsh
λ yarn list react-scripts
yarn list v1.22.0
```

Since `2.1`, TypeScript is supported, so upgrade to the lastest version with:

```zsh
λ yarn upgrade react-scripts --latest

• • •

✨  Done in 9.41s.
```

[⬆ Back to index](#index)

---

### Removing `ESlint` packages

`react-scripts` will take care of the using the correct versions of `ESlint`, so we can remove them from the `package.json`:

```zsh
λ yarn remove eslint eslint-config-react-app eslint-plugin-flowtype eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-react

• • •

success Uninstalled packages.
✨  Done in 8.96s.
```

[⬆ Back to index](#index)

---

### Adding TypeScript

Add TypeScript with:

```zsh
λ yarn add typescript @types/node @types/react @types/react-dom @types/jest @types/react-router @types/react-router-dom

• • •

✨  Done in 4.92s.
```

Rename every `.js` file to `.tsx` so you'll have to following folder structure in `ClientApp/src`:

```zsh
lt-project-structure/ClientApp/src
├── components
│   ├── Counter.tsx
│   ├── FetchData.tsx
│   ├── Home.tsx
│   ├── Layout.tsx
│   ├── NavMenu.css
│   └── NavMenu.tsx
├── App.test.js
├── App.tsx
├── custom.css
├── index.tsx
├── react-app-env.d.ts
└── registerServiceWorker.js
```

Run the project with `dotnet run`. .NET will automatically generate a `tsconfig.json` file.

```zsh
We detected TypeScript in your project (src/App.tsx) and created a tsconfig.json file for you.
```

Modify `index.tsx` so the `BrowserRouter` has the `basename` as such:

```ts
ReactDOM.render(
  <BrowserRouter basename={baseUrl || ''}>
    <App />
  </BrowserRouter>,
  rootElement);
```

At this point, TypeScript will complain. It's up to you if you'd like to fix those or remove all the boilerplate files. If you decide to remove the boilerplate code, leave everything outside the `components` folder.

[⬆ Back to index](#index)

---