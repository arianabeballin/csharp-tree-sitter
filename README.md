# csharp-tree-sitter
==================

## Introduction
This module provides C# bindings to the [tree-sitter](https://github.com/tree-sitter/tree-sitter) parsing library, which can enable c# developers be able to invoke the tree-sitter libraries through P/Invoke from their c# code.

## Cloning

This repo includes the needed tree-sitter repos as submodules.  Remember to use the `--recursive` option with git clone.

```cmd
git clone https://github.com/tree-sitter/csharp-tree-sitter.git --recursive
```

## Building

Requirements:
- Windows with MSVC command-line tools (`cl` and `nmake`) available
- .NET 7 SDK

Build the native tree-sitter DLLs first, then build the C# project:

```cmd
cd tree-sitter
nmake
cd ..
dotnet build csharp-tree-sitter.csproj
```

The native build writes `tree-sitter.dll` and `tree-sitter-cpp.dll` to `bin\Debug\net7.0`, which is where the C# app and VS Code launch configuration expect them.

## Running the parser demo

The sample in `tests/test.cs` walks a parse tree using the `tree-sitter-cpp` grammar through these bindings.

Assuming you're in VS Code:
- open `.vscode/launch.json`
- replace the placeholder `"path"` argument with one or more real C/C++ file paths
- press `F5` and choose the `test` launch configuration

From a terminal, run the built assembly directly:

```cmd
dotnet bin\Debug\net7.0\csharp-tree-sitter.dll -files [your test cpp files]
```

## Contributing

- Keep submodules up to date (see `/tree-sitter/README.md`).
- Ensure `nmake` and `dotnet build` both succeed before opening a change.
