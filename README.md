# debrepo

A Debian repository includes necessary packages for HardenedLinux. Of HardenedLinux,
by HardenedLinux, for HardenedLinux.

# Using the Repo

Add the following lines to your `/etc/apt/sources.list` to start using the
repository.


    deb http://hardenedlinux.org/debrepo/ jessie main
    deb-src http://hardenedlinux.org/debrepo/ jessie main


Then, import the signing key to your system keyring.


    apt-key adv --fetch-keys https://tomli.blog/pubkey.asc


Please note that currently the repository is hosted on GitHub, HTTPS is not
supported. You are expected to change the address as we ready to publish the
repository on a separate domain.

# Architecture

Currently, `amd64` is the only supported architecture. As more and more programs
and Linux distributions are dropping x86 support, it is unlikely that x86 would
be supported by this repository. In addition, this repository is focused on
packages for web servers, nowadays, x86 is barely used for servers due to the
lack of computing power.

However, if you have a valid reason for supporting x86, and you are willing to
do the testing, feel free to open an issue ticket.

# Packages

For now, the included packages are:

* elfix
    * Utilities to modify Elf binaries to work with PaX hardened kernel, such as
    `paxctl-ng`.
    * Source: https://github.com/hardenedlinux/elfix-deb

Stay tuned for update!

# Pull Request

Pull Requests will NOT be accepted, since all packages and repo changes require to
be signed by the maintainer. A package is included if and only if the packaging
task is a project of HardenedLinux.

You may consider joining HardenedLinux by creating an issue, and make your packaging
task a project of HardenedLinux. However, packaging and publishing are still made by
the maintainer(s) alone.

# Security

When a security update came out but the repository is not updated yet, you can create
an issue requesting security updates.

If you find any vulnerabilities within the repository itself, please do NOT post an
issue ticket, instead, send an PGP-encrypted mail using the PGP Key and E-mail address
showed above!

# Signing Key

The packager, maintainer and publisher of the repository is Tom Li, contents
in this repository are signed with the following PGP key. All git commits are
also signed by the same key.

    pub   rsa4096 2015-01-01 [SC]
          2552 11B2 395A 5A3E 0E48  A0F1 FAD3 EB05 E88E 8D6D
    uid           Yifeng Li (Tom Li) <tomli@tomli.me>
    uid           Yifeng Li (Tom Li, or biergaizi) <biergaizi2009@gmail.com>
    uid           Yifeng Li (Tom Li) <biergaizi@member.fsf.org>
    sub   rsa4096 2015-01-01 [E]
    sub   rsa4096 2015-01-01 [A]

If you are verifying and auditing the repository, you should always check the
fingerprint of the signing key and NEVER TRUST THE SHORT KEY-ID. To avoid
malicious modifications of the public key for online phishing, the public
key is hosted in three individual places.

    # Blog
    gpg --fetch-keys https://tomli.blog//pubkey.asc

    # Keybase
    gpg --fetch-keys https://keybase.io/biergaizi/key.asc

    # MIT Keyserver
    gpg --keyserver hkp://pgp.mit.edu --recv-key 255211b2395a5a3e0e48a0f1fad3eb05e88e8d6d

If you find the keys are unmatched, this might indicate a malicious phishing or MITM
attack, report an issue immediately!

