---
layout: documentation
title: Installing Bazel on Ubuntu
---

# <a name="ubuntu"></a>Install Bazel on Ubuntu

Supported Ubuntu Linux platforms:

*   16.04 (LTS)
*   14.04 (LTS)

Install Bazel on Ubuntu using one of the following methods:

*   [Use our custom APT repository (recommended)](#install-on-ubuntu)
*   [Use the binary installer](#install-with-installer-ubuntu)
*   [Compile Bazel from source](install-compile-source.html)

Bazel comes with two completion scripts. After installing Bazel, you can:

*   access the [bash completion script](install.html)
*   install the [zsh completion script](install.html)

## <a name="install-on-ubuntu"></a> Using Bazel custom APT repository (recommended)

### 1. Install JDK 8

Install JDK 8 by using:

```bash
sudo apt-get install openjdk-8-jdk
```

On Ubuntu 14.04 LTS you'll have to use a PPA:

```bash
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update && sudo apt-get install oracle-java8-installer
```

### 2. Add Bazel distribution URI as a package source (one time setup)

```bash
echo "deb [arch=amd64] http://storage.googleapis.com/bazel-apt stable jdk1.8" | sudo tee /etc/apt/sources.list.d/bazel.list
curl https://bazel.build/bazel-release.pub.gpg | sudo apt-key add -
```

If you want to install the testing version of Bazel, replace `stable` with
`testing`.

### 3. Install and update Bazel

```bash
sudo apt-get update && sudo apt-get install bazel
```

Once installed, you can upgrade to a newer version of Bazel with:

```bash
sudo apt-get upgrade bazel
```

## <a name="install-with-installer-ubuntu"></a>Install using binary installer

The binary installers are on Bazel's [GitHub releases page](https://github.com/bazelbuild/bazel/releases).

The installer contains the Bazel binary and the required JDK. Some additional
libraries must also be installed for Bazel to work.

### 1. Install required packages

```bash
sudo apt-get install pkg-config zip g++ zlib1g-dev unzip python
```

### 2. Download Bazel

Go to Bazel's [GitHub releases page](https://github.com/bazelbuild/bazel/releases).

Download the binary installer `bazel-0.5.4-installer-linux-x86_64.sh`. This
installer contains the Bazel binary and the required JDK, and can be used even
if JDK is already installed.

Note that `bazel-0.5.4-without-jdk-installer-linux-x86_64.sh` also exists.
It is a version without embedded JDK 8. Only use this installer if you already
have JDK 8 installed.

### 3. Run the installer

Run the installer:

```bash
chmod +x bazel-0.5.4-installer-linux-x86_64.sh
./bazel-0.5.4-installer-linux-x86_64.sh --user
```

The `--user` flag installs Bazel to the `$HOME/bin` directory on your system and
sets the `.bazelrc` path to `$HOME/.bazelrc`. Use the `--help` command to see
additional installation options.

### 4. Set up your environment

If you ran the Bazel installer with the `--user` flag as above, the Bazel
executable is installed in your `$HOME/bin` directory. It's a good idea to add
this directory to your default paths, as follows:

```bash
export PATH="$PATH:$HOME/bin"
```

You can also add this command to your `~/.bashrc` file.
