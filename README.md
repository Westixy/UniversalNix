# UniversalNix

Nix is were you can find almost any package you want. But you need nix. Well in reality you can bundle a nix package to a single file
(containing all dependencies, so no clash with others dependencies, but might be heavy). Wouldn't it be nice to have a repository for
deb and rpm that has this power from a simple `apt install uninix-<whatever>` ?  let's build it!

NB: this project will start the 1st of July 2024 for the [Backdrop Build event](https://backdropbuild.com)

## Interface expected (from simple to crazy time consuming)

1. PoC: `nix run .#uninix make-deb <flakepath>` returns a `.deb` file of the selected promgram
2. PoC2: `nix run .#uninix make-rpm <flakepath>` returns a `.rpm` file of the selected promgram
3. probably some smaller steps in between
4. MVP: `nix run .#uninix serve deb` starts a debian repository that we can run `apt-get install uninix-<flakepath>` (needs to define how to prebuild or select which version to build)
5. MVP2: `nix run .#uninix serve rpm` starts a debian repository that we can run `yum install uninix-<flakepath>` (needs to define how to prebuild or select which version to build)
6. and probaly more ?
