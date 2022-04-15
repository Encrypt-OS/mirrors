# Mirrors for EncryptOS


[![Maintenance](https://img.shields.io/maintenance/yes/2022.svg)]()

```
######################################################
####                                              ####
###           EncryptOS  Mirror List               ###
####                                              ####
######################################################
#### Entry in file /etc/pacman.conf:
###     [encryptos]
###     SigLevel = PackageRequired
###     Include = /etc/pacman.d/encryptos-mirrorlist
######################################################
### Tip: Use the 'eos-rankmirrors' program to rank
###      these mirrors or re-order them manually.
######################################################

## GitHub
Server = https://raw.githubusercontent.com/Encrypt-OS/repo/main/$repo/$arch
```

## Github Fallbacks
Note: the usage of the github "mirrors" below is *not* recommended. They are likely to be removed soon.
```
https://raw.githubusercontent.com/Encrypt-OS/repo/main/$repo/$arch

https://github.com/Encrypt-OS/mirrors/releases/download/mirror1
https://github.com/Encrypt-OS/mirrors/releases/download/mirror2
```

## Default `pacman.conf`
To update from older installs:
```
wget https://raw.githubusercontent.com/Encrypt-OS/EncryptOS-ISO/main/airootfs/etc/pacman.conf && sudo cp pacman.conf /etc/
```
```
#
# /etc/pacman.conf
#
# See the pacman.conf(5) manpage for option and repository directives

#
# GENERAL OPTIONS
#
[options]
# The following paths are commented out with their default values listed.
# If you wish to use different paths, uncomment and update the paths.
#RootDir     = /
#DBPath      = /var/lib/pacman/
#CacheDir    = /var/cache/pacman/pkg/
#LogFile     = /var/log/pacman.log
#GPGDir      = /etc/pacman.d/gnupg/
#HookDir     = /etc/pacman.d/hooks/
HoldPkg     = pacman glibc
#XferCommand = /usr/bin/curl -L -C - -f -o %o %u
#XferCommand = /usr/bin/wget --passive-ftp -c -O %o %u
#CleanMethod = KeepInstalled
#UseDelta    = 0.7
Architecture = auto

# Pacman won't upgrade packages listed in IgnorePkg and members of IgnoreGroup
#IgnorePkg   =
#IgnoreGroup =

#NoUpgrade   =
#NoExtract   =

# Misc options
#UseSyslog
Color
ILoveCandy
#NoProgressBar
#CheckSpace
VerbosePkgLists
DisableDownloadTimeout
ParallelDownloads = 10

# By default, pacman accepts packages signed by keys that its local keyring
# trusts (see pacman-key and its man page), as well as unsigned packages.
SigLevel    = Required DatabaseOptional
LocalFileSigLevel = Optional
#RemoteFileSigLevel = Required

# NOTE: You must run `pacman-key --init` before first using pacman; the local
# keyring can then be populated with the keys of all official Arch Linux
# packagers with `pacman-key --populate archlinux`.

#
# REPOSITORIES
#   - can be defined here or included from another file
#   - pacman will search repositories in the order defined here
#   - local/custom mirrors can be added here or in separate files
#   - repositories listed first will take precedence when packages
#     have identical names, regardless of version number
#   - URLs will have $repo replaced by the name of the current repo
#   - URLs will have $arch replaced by the name of the architecture
#
# Repository entries are of the format:
#       [repo-name]
#       Server = ServerName
#       Include = IncludePath
#
# The header [repo-name] is crucial - it must be present and
# uncommented to enable the repo.
#

# The testing repositories are disabled by default. To enable, uncomment the
# repo name header and Include lines. You can add preferred servers immediately
# after the header, and they will be used before the default mirrors.

#[testing]
#Include = /etc/pacman.d/mirrorlist

[core]
Include = /etc/pacman.d/mirrorlist

[extra]
Include = /etc/pacman.d/mirrorlist

#[community-testing]
#Include = /etc/pacman.d/mirrorlist

[community]
Include = /etc/pacman.d/mirrorlist

# If you want to run 32 bit applications on your x86_64 system,
# enable the multilib repositories as required here.

#[multilib-testing]
#Include = /etc/pacman.d/mirrorlist

[multilib]
Include = /etc/pacman.d/mirrorlist

[encryptos]
SigLevel = PackageRequired
Include = /etc/pacman.d/EncryptOS-mirrorlist

# An example of a custom package repository.  See the pacman manpage for
# tips on creating your own repositories.
#[custom]
#SigLevel = Optional TrustAll
#Server = file:///home/custompkgs

```
