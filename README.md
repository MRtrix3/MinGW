# For users:

Regular users are probably more interested in installing the precompiled packages. Please see [the relevant page on the main MRtrix3 wiki for instructions](https://www.mrtrix.org/download/windows-msys2/).

# For package maintainers:

Main usage should take the form:
```
./run.sh 3.0.8 mrtrix3
```
Where:
- `3.0.8` is the specific tag or branch to be built
- `mrtrix3` is the user or organisation name of the GitHub repo from which to fetch the MRtrix3 source code

## PKGBUILD file for MSYS2

This is used to create the installable MRtrix3 package on MSYS2. This will only
create the x86-64 version of the package. To use it, clone this repo and invoke
the `makepkg` command within the toplevel folder:

```
git clone https://github.com/MRtrix3/MinGW.git
cd MinGW/
makepkg
```

This will generate the package file, which can be installed using this command
(edit as appropriate):

```
pacman -U mingw-w64-x86_64-mrtrix3-3.0_RC3-1-x86_64.pkg.tar.xz
```

