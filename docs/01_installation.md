# Installation

## Install Git

### Windows

### Linux

## Initial setting

### Set committer

``` bash
git config --global set user.email <Your e-mail address>
git config --global set user.name <Your name>
```

### Generate GPG key

1. Install GPG command

    ``` bash
    apt-get install gnupg
    ```

    On Windows, need to execute this command in bash.

2. Generate GPG key-pair

    ``` bash
    gpg --full-generate-key
    ```

3. Select key type or press `Enter` key
4. Input key size

    Key size is to need to set `4096` bit.

5. Enter the length of time the key should be valid.
6. Verify that your selections are correct.
7. Enter your user ID information

    :notebook: When asked to enter your email address, ensure that you enter the verified email address for your GitHub account

8. Type a secure passphrase.
9. Copy GPG key id

    In this example, copy `3AA5C34371567BD2`.

    ``` bash
    gpg --list-secret-keys --keyid-format LON
    /Users/hubot/.gnupg/secring.gpg
    ------------------------------------
    sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
    uid                          Hubot 
    ssb   4096R/42B317FD4BA89E7A 2016-03-10
    ```

10. To set GPG signing key in Git

    ``` bash
    git config --global user.signingkey 3AA5C34371567BD2
    ```

11. Add profile

    ```bash
    if [ -r ~/.bash_profile ]; then echo 'export GPG_TTY=$(tty)' >> ~/.bash_profile; \
    else echo 'export GPG_TTY=$(tty)' >> ~/.profile; fi
    ```
