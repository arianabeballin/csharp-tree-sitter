# Update the submodules

This repository tracks nested tree-sitter sources as submodules. From the repository root, refresh submodule pointers and fetch their latest configured upstream commits with:

```cmd
git pull
git submodule update --init --recursive --remote
```
