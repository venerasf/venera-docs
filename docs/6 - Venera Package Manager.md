# Venera Package Manager

The `vpm` is a command that allows you to manage the scripts in your base. It has the main function of synchronizing scripts with a remote repository, therefore the user can select a repository and download some specific scripts, or even all of them.

> [!faq] The default repository is `http://r.venera.farinap5.com/package.yaml`

The file `package.yaml` contains the references to the scripts. This file could have any name, so it must be written correctly.

>[!faq] The file `package.sgn` has the signature for verification

This will be used to check if there has been any compromise in the scripts. Must be changed with caution. Verification is done based on trust for that author who has signed the package. Your installation must trust that author, so that the scripts are downloaded.
## Basic Commands

VPM has any commands for managing the scripts.
### Search Scripts

Use the command `search <pattern>` to see all scripts matching with given pattern.

```
[vnr]>> vpm search cve
[OK]- Requesting http://r.venera.farinap5.com/package.yaml

[OK]- 18 scripts found.
-----------------------
Script:         /cve/cve-2014/CVE-2014-6271.lua
Version:        1.000000
Decription:
Tags:           tags
-----------------------
Script:         /cve/cve-2021/CVE-2021-40978.lua
Version:        1.000000
Decription:
Tags:           tags
[OK]- 2 scripts.
```

### Download One Script

Use the command `install <script path>` download one script from the remote repository.

```
[vnr]>> vpm install /cve/cve-2014/CVE-2014-6271.lua
[OK]- Requesting http://r.venera.farinap5.com/package.yaml

[OK]- /cve/cve-2014/CVE-2014-6271.lua installed.
[vnr]>>
```
### Verify Repo Signature

The command `verify` may be used to see if the signature of `package.yaml` can be trusted and has been created by a trusted author as it says. It works because Venera has the author's public key installed, will use it to verify if the hash in file `package.sgn` (containing `package.yam` signature) is valid and has been signed by that auth's private key.

```
[vnr]>> vpm verify
[OK]- Getting key for author: elf@mail.com
[OK]- Sign date: 2021-8-15 14:30:45
[OK]- Signed by trusted author: elf@mail.com
[vnr]>>
```

### Synchronize With Remote Repo

Use the `sync` command to download all scripts from the remote repository and get the last version.

```
[vnr]>> vpm sync
[OK]- Requesting http://r.venera.farinap5.com/package.yaml
```
## Set Remote Repository

The remote repository is taken from [[4 - Global Variables]], so from there you can set another server from where VPM will look for codes.

For instance, if you have a repository on the local network for your team, you can set that repository as the default source using the following commands.

Set the repository:

```
[vnr]>> globals set repo http://0.0.0.0/package.yaml
[vnr]>> globals set sign http://0.0.0.0/package.sgn
[vnr]>> globals

VARIABLE   VALUE
--------   -----
...
sign       http://0.0.0.0/package.sgn
repo       http://0.0.0.0/package.yaml
...
```

>[!info] You must set a signature (`globals set sign`) resource or disable it!

To disable the signature verification, change the value in `vpmvs` to `false`. Return to `true` enable the verification.