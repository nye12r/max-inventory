# max-inventory

An example project Go with clean Architecture

# devops-pipeline-params-pre-example

![go](https://img.shields.io/badge/GO-V%201.18-blue)
>A simple Config Params Pipeline example. `:wq`
>
>`git-crypt` enables transparent encryption and decryption of files in a git repository. Files which you choose to protect are encrypted when committed, and decrypted when checked out. `git-crypt` lets you freely share a repository containing a mix of public and private content.
>
>Developed with all :heart: in the world by ADL DevOps team

## Table of Content

- [Prerequisites](#Prerequisites)
- [For all collaborators](#For-all-collaborators)
- [For team Architects](#For-team-Architects)
- [So, the repo is ready, now What?](#So-the-repo-is-ready--now-What-)
- [Contributing](#Contributing)
- [Further Reading / Useful Links](#Further-Reading--Useful-Links)

## Prerequisites

You will need the following things properly installed on your computer.

- [git](http://git-scm.com/)
- [git-crypt](https://github.com/AGWA/git-crypt)
- [GPG](https://gnupg.org/)

## For all collaborators

Every collaborators needs to generate their own GPG key pairs & then needs to be shipped to any user who already have the authority to add users to and encrypted repo, for example; **Your team Architect!**

### Install git-crypt with Homebrew

```bash
brew install git-crypt
```

### Install GPG with Homebrew

```bash
brew install gpg
```

### Generating your GPG key

The first step to use GnuPG is to create the `Public` and `Private` key pairs.

The following command is used to create the keys:

```bash
gpg --gen-key
```

This will prompt you for your `Name`, `Email` and `Pass-phrase`:

- **Name:** Please use your full name, i.e. *Covid Pepito Perez Rodriguez*
- **Email:** Will uniquely identify you. Please use your *ADL* email. e.g. *covid.perez@avaldigitallabs.com*
- **Pass-phrase:** Make sure you enter a strong one. You again need to confirm the pass-phrase

After generating the keys, you can get information about it use `list-keys` command:

```bash
gpg --list-keys
```

You will get output something like this:

```console
$ gpg --list-keys

/Users/covid.perez/.gnupg/pubring.kbx
----------------------------------
pub   rsa2048 2020-07-29 [SC] [expires: 2022-07-29]
      B44DABCCD78435E7F4E9676416DC869402E26669
uid           [ultimate] Covid Pepito Perez Rodriguez <covid.perez@avaldigitallabs.com>
sub   rsa2048 2020-07-29 [E] [expires: 2022-07-29]
```

You need to get the `Public` key which is a hexadecimal string in the previous command. In this case it is :point_right: `B44DABCCD78435E7F4E9676416DC869402E26669`.

### Exporting your GPG key

Next step is to export your `Public` key to a GPG file. Using the `export` command:

```bash
gpg --armor --export --output covid_perez.gpg B44DABCCD78435E7F4E9676416DC869402E26669
```

This step will generate a GPG file called name `covid_perez.gpg` in the current directory. This GPG file looks like this:

```console
$ cat covid_perez.gpg

-----BEGIN PGP PUBLIC KEY BLOCK-----

mQENBF8htlMBCADQJ/tvbCZdH+8lIDNb3CmwrlhBCp10YuWejHIe7ekB0i09Cu0w
mYMib51eatOwkqho/AHJWiXZDr1EpfRGjGZsOeKq2Ody743XJZ87Uxehufi/lGeL
StYsBpXWJY1/NyhAWm/e8jqrmfiISpTxD30IbRqX/88A8tfbJLxRYw6I5Mt4Unhs
lluVp5uDlmJby7yYuKI3NGAzYSkiJu64HAFYTIGFHNMH2GQs0g590qEAZJLaEUru
B7DoRjVn4ptFs3n7m+VLQKZxrY/XxFtStkigw114YIoAgiaxW7tMrqIH9XuGpFg1
a7fSElhlQhVIhDF3pNLhV9e7dM9AW3nWXVB5ABEBAAG0PkNvdmlkIFBlcGl0byBQ
ZXJleiBSb2RyaWd1ZXogPGNvdmlkLnBlcmV6QGF2YWxkaWdpdGFsbGFicy5jb20+
iQFUBBMBCAA+FiEEtE2rzNeENef06WdkFtyGlALiZmkFAl8htlMCGwMFCQPCZwAF
CwkIBwIGFQoJCAsCBBYCAwECHgECF4AACgkQFtyGlALiZmkuFAf/XOalhT6UV67Q
aZpYRLCXoovVOoCx0DSH30/H+I3httJJ5ndGG2GiZ9zXAdmD+3LKMGUdUIyj5Mvc
+hjNiIjxrFU4TWfA5hiI7OZ3uNWjRQknHfFJzBmvDvkvodEAIqfv7DE2S1oFIq12
hHFRW6fuhaLvzz5fnY8lPpKRFtyU01Cp7dI3OtofQR8g7R/1yQmP3yf5DAsGyx5J
kCUmpmkLGXw0b2xp8h07q0YtZ92O/GzOBVlD7vy/ej1mpAqHPVqk84FjdDB0ufSp
ClQbFuZLEBZ5OidaEpHB3QeDA5blLMnPzs7So1d2E1Aeosmx1y+u5BaBTwvgtGyo
xFM00EB6ArkBDQRfIbZTAQgAwAWKtsx8gedGMfsk2rfb5w4P5bXrYCY6xx0IYvGA
KvCaM4n1PUZea1vaCkSTY9KjMCwk+z0VnoCS8L/fZe9Ogu5/I7UktOqOpSblDSUu
1lJygJYjuSwj33XsC3rMzvLzcqErT9xOBzvhqqhBkB4r3BQrH/G5v8jzfLpus+P/
TU++isAS/V71P0ZKRdUojaT65TT+/gHLJtBRCtgm0RzD+9FMIe1d6VPfFP/c7NmZ
pvkygaltIe/uGo97m7bfYxJ2VUfaULNWk9f9sj+VXOYiZU9s0D9XVX5ZX9qIaZZl
vBKO9Gw0t5M3OgFp3cOiT/Gw4KN5fOFyTWWip91J74IKGQARAQABiQE8BBgBCAAm
FiEEtE2rzNeENef06WdkFtyGlALiZmkFAl8htlMCGwwFCQPCZwAACgkQFtyGlALi
ZmnA2QgAokbT2XCPcgWPmTO2sokPGbN7CpCNrAiJdrS6nkjT74Y8ikZa0IwLitMU
x4uqSMJugvknaa1cT4yfY+4gLPyGnfDSZRdspzHCPCaaAC/aNu2jYtRxJcMpQqpF
PhnmZ55mZEydYaMgcStYEcKnJxvbKOOqJ9kZz6TC0CrNxZC7OviNv20AtmcPfDK8
mBHKZ0/RaDq1JzUk4Ly2PBDk1ldgIIWjOwUYwjPto7brz0ZEjb/gQ+IxibYTyPpE
5scjAuSrFeiBQf78qRCsvLYXq6sI14Jz4AjCVcbvbhm0n2qsksHjmZULqxHQs43i
ZH84R+vuqdgocUy7zd4PRQkAmHalOQ==
=xrFV
-----END PGP PUBLIC KEY BLOCK-----
```

After this final step, are you ready to share your collaborator `Public` GPG file with your team Architect!

## For team Architects

1. First off all, you need to clone the new created repo, change to the src code repo and initialise `git-crypt`. This init step should be executed only one time in the entire repository life.

2. Adding collaborators to an encrypted repo is easy, you need to import the collaborator's `Public` key in order to add the key to the "repo" `Keyring` then trust it and finally add the collaborator to the encrypted repo.

3. Don't Forget to add the @devops-security-team (Hackers Team) and Jenkins CI/CD `Public` keys to the "repo" `Keyring` just as another repo collaborator.

4. Finally, You can `git push` the repo and the new encryption will be pushed out.

### 1. Initialising the repo

This will initialise `git-crypt` in the new repository, but *it does not encrypt any files by default*. `git_crypt` uses the `.gitattributes` file to define what files it will manage.

Naturally, you want to do this before you create the sensitive files.

```console
$ git clone git@github.avaldigitallabs.com:avaldigitallabs/devops-pipeline-params-pre-example.git

Cloning into 'devops-pipeline-params-pre-example'...
remote: Enumerating objects: 120, done.
remote: Counting objects: 100% (120/120), done.
remote: Compressing objects: 100% (84/84), done.
remote: Total 120 (delta 29), reused 103 (delta 23), pack-reused 0
Receiving objects: 100% (120/120), 40.89 KiB | 307.00 KiB/s, done.
Resolving deltas: 100% (29/29), done.

$ cd devops-pipeline-params-pre-example

$ git-crypt init

Generating key...
```

This will also generate `.git-crypt` folder in your root repo which will contain the public keys of collaborators.

### 2.1 Importing a collaborator Public key

For this use GPG `import` command:

```bash
gpg --import covid_perez.gpg
```

You will get output something like this (Please verify name and ADL email :pray:):

```console
$ gpg --import covid_perez.gpg

gpg: key 16DC869402E26669: public key "Covid Pepito Perez Rodriguez <covid.perez@avaldigitallabs.com>" imported
gpg: Total number processed: 1
gpg:               imported: 1
```

After importing the collaborator `Public` key, you can get information about all available keys with `list-keys` command:

```bash
gpg --list-keys
```

You will get output something like this (look the `unknown` trusted level :sweat: down bellow):

```console
$ gpg --list-keys

/Users/andres.amado/.gnupg/pubring.kbx
----------------------------------
pub   rsa2048 2020-07-29 [SC] [expires: 2022-07-29]
      B44DABCCD78435E7F4E9676416DC869402E26669
uid           [ unknown] Covid Pepito Perez Rodriguez <covid.perez@avaldigitallabs.com>
sub   rsa2048 2020-07-29 [E] [expires: 2022-07-29]
```

### 2.2 Trustting a collaborator imported Public key

Next step is to add trust to the collaborator `Public` key with `edit–key` command:

This will lead to a GPG prompt where you can get the fingerprint of the collaborator `Public` key by using `fpr` command:

Add trust level to collaborator by `trust` command. It will ask for a trust level to select, add accordingly.

```console
$ gpg --edit-key B44DABCCD78435E7F4E9676416DC869402E26669

gpg (GnuPG) 2.2.21; Copyright (C) 2020 Free Software Foundation, Inc.
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.


pub  rsa2048/16DC869402E26669
     created: 2020-07-29  expires: 2022-07-29  usage: SC
     trust: unknown       validity: unknown
sub  rsa2048/DC7D99575644AFB6
     created: 2020-07-29  expires: 2022-07-29  usage: E
[ unknown] (1). Covid Pepito Perez Rodriguez <covid.perez@avaldigitallabs.com>

gpg> fpr
pub   rsa2048/16DC869402E26669 2020-07-29 Covid Pepito Perez Rodriguez <covid.perez@avaldigitallabs.com>
 Primary key fingerprint: B44D ABCC D784 35E7 F4E9  6764 16DC 8694 02E2 6669

gpg> trust B44D ABCC D784 35E7 F4E9  6764 16DC 8694 02E2 6669
pub  rsa2048/16DC869402E26669
     created: 2020-07-29  expires: 2022-07-29  usage: SC
     trust: unknown       validity: unknown
sub  rsa2048/DC7D99575644AFB6
     created: 2020-07-29  expires: 2022-07-29  usage: E
[ unknown] (1). Covid Pepito Perez Rodriguez <covid.perez@avaldigitallabs.com>

Please decide how far you trust this user to correctly verify other users' keys
(by looking at passports, checking fingerprints from different sources, etc.)

  1 = I don't know or won't say
  2 = I do NOT trust
  3 = I trust marginally
  4 = I trust fully
  5 = I trust ultimately
  m = back to the main menu

Your decision? 5
Do you really want to set this key to ultimate trust? (y/N) y

pub  rsa2048/16DC869402E26669
     created: 2020-07-29  expires: 2022-07-29  usage: SC
     trust: ultimate      validity: unknown
sub  rsa2048/DC7D99575644AFB6
     created: 2020-07-29  expires: 2022-07-29  usage: E
[ unknown] (1). Covid Pepito Perez Rodriguez <covid.perez@avaldigitallabs.com>
Please note that the shown key validity is not necessarily correct
unless you restart the program.

gpg>
```

After verifying the fingerprint save & quit changes by `save` command:

```console
gpg> save
```

Quit the prompt by `quit` command:

```console
gpg> quit
```

### 2.3 Adding a collaborator to the encrypted repo

Now you have added and trusted the collaborator's `Public` key to your `Keyring`, all that’s left to do is add that `Public` key to the repo. You can do that with the `add-gpg-user` command. This will not only add the collaborator’s `Public` key as a verified decrypted but also serves as a git commit.

```console
$ git-crypt add-gpg-user B44DABCCD78435E7F4E9676416DC869402E26669

$ git log --oneline -n 1

23963ed (HEAD -> master, origin/master, origin/HEAD) Add 1 git-crypt collaborator
```

### 3. Adding Hackers Team & Jenkins CICD to the encrypted repo

Add the @devops-security-team (Hackers Team) and Jenkins CI/CD `Public` keys to the "repo" `Keyring`  as another repo collaborator. This process is exactly the same previous steps using the GPG files located in the `keys` folder.

```console
$ tree -L 3

.
├── LICENSE
├── README.md
├── docs
│   ├── CHANGELOG.md
│   ├── CODE_OF_CONDUCT.md
│   └── PROCESS.md
├── keys
│   ├── jenkins_cicd.gpg        # Jenkins CI/CD GPG jey
│   ├── jhon_triana.gpg         # Jhon Triana Hacker GPG jey
│   └── oscar_martinez.gpg      # Oscar Martínez Hacker GPG jey
├── params                      # Public no sensitive YML params folder
│   ├── dev                     # Public no sensitive DEV environment YML params folder
│   │   ├── auth.yml
│   │   ├── commons.yml
│   │   └── payments.yml
│   └── stg                     # Public no sensitive STG environment YML params folder
│       ├── auth.yml
│       ├── commons.yml
│       └── payments.yml
└── secrets                     # Private sensitive YML secrets folder
    ├── dev                     # Private sensitive DEV environment YML secrets folder
    │   ├── auth.yml
    │   ├── commons.yml
    │   └── payments.yml
    └── stg                     # Private sensitive STG environment YML secrets folder
        ├── auth.yml
        ├── commons.yml
        └── payments.yml

8 directories, 20 files
```

For example, after importing and trust the Jenkins CI/CD GPG file, You will probably execute:

```bash
git-crypt add-gpg-user DAD1E51F1209751FD2F1BB4C9C848B9BB871610E
```

### 4. Pushing your repo setup

At this point, you can `git push` your feature branch, create a PR to `master` branch, and the new encryption will be pushed out after merge the PR :muscle:.

## So, the repo is ready, now What?

For all collaborators, after cloning the repo, all files mentioned in the `.gitattributes` file will be encrypted. You can unlock files by `unlock` command:

```bash
git-crypt unlock
```

You should only execute this `unlock` step after clone the repo, then all files will be encrypted before `push` and decrypted after `pull` from the repo.

What? From now on the files will be automatically encrypted on every `push`, i.e. you will be able to read and edit them in your local working copy, but on the remote and in other working copies the files will be encrypted.

`git-crypt` gracefully degrades, so developers without the secret key can still clone and commit to a repository with encrypted files.

**Summary:** After unlock the repo, you can use it as any other repo :wink:

>:cop: WE STRONGLY RECOMMEND PLAY WITH THIS ENCRYPTED REPO IN CONSOLE/TERMINAL WAY. :cop:
>
> *This lets you store your secret material (such as keys or passwords) in the same repository as your code, without requiring you to lock down your entire repository.*
>
>:rotating_light: Be carefull if you are using a Git UI or Git "fancy" client :rotating_light:

## Contributing

If you find this repo useful here's how you can help:

1. Send a Merge Request with your awesome new features and bug fixes
2. Wait for a Coronita :beer: you deserve it.

## Further Reading / Useful Links

- [Securing your secret keys with git-crypt](https://medium.com/@sumitkum/securing-your-secret-keys-with-git-crypt-b2fa6ffed1a6)  **(This README file is base on it!)*
- [Transparent file encryption in git](https://github.com/AGWA/git-crypt)
- [THow to secure sensitive data with git-crypt](https://buddy.works/guides/git-crypt)
