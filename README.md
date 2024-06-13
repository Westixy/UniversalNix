# UniversalNix

Nix is were you can find almost any package you want. But you need nix. Well in reality you can bundle a nix package to a single file
(containing all dependencies, so no clash with others dependencies, but might be heavy). Wouldn't it be nice to have a repository for
deb and rpm that has this power from a simple `apt install uninix-<whatever>` ?  let's build it!

NB: this project will start the 1st of July 2024 for the [Backdrop Build event](https://backdropbuild.com)

## Interface expected (from simple to crazy time consuming)

1. PoC: `nix run .#uninix make-deb <flakepath>` returns a `.deb` file of the selected promgram
  2. optional: `nix run .#uninix make-rpm <flakepath>` returns a `.rpm` file of the selected promgram
3. MVP: create a service that can prebuild and push the deb file to an existing deb or rpm repo (ex: github/gitlab debian repo)
4. deb repo: `nix run .#uninix serve deb` starts a debian repository that we can run `apt-get install uninix-<flakepath>` (aptly pluging might simpler)
  5. optional: rpm repo: `nix run .#uninix serve rpm` starts an rpm repository that we can run `yum install uninix-<flakepath>` 

## Implementations ideas

- mvp: use a existing repository like github or gitlab one, and add an external service that will fill up the deb package repository by a simple curl to the service
- Create a plugin for [aptly](https://www.aptly.info/) for deb
  - pro: no need to reimplement full deb registry
  - con: no rpm (but not sure i want to handle rpm just now)
