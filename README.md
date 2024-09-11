# install_infrastructure_at_tacc
Description of how Victor installs software at TACC

In the jail of each cluster there is a directory `victor_scripts` that contains
 - a `make_download` script.
 - a repository of makefiles
 - a repository of spec files
 - a repository of make support files
 - a `pull_all.sh` script for updating the repositories, and customizing the cluster-specific install script

After downloading:

```
victor_scripts/make_download fftw3
```

you then generate and install rpms with:

```
victor_scripts/tacc_specfiles/<CLUSTER>_specfiles/install.sh [-m] package
```

where the `-m` option is needed for MPI-dependent packages.

## Version and release numbers

There is a file `versions.txt` that should probably go.

Package version number is maintained in the spec file, makefile, and versions file.
Though the spec file invokes the makefile with an explicit version number, so 
the makefile can be out of sync.

The release number of the rpm is in the spec file and the versions file.

## Installation location

Each cluster has a slightly different naming convention for the location of packages.
The `pull_all.sh` script generates the cluster-specific spec files from the general repository.


