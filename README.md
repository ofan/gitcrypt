gitcrypt
========

Gitcrypt is a set of scripts used to encrypt and decrypt automatically for you git repositories.

Installation
===

Put `fnmatch`, `git_crypt_filter` in one of your $PATH directories.

Usage
===
1. Create a new git repository.

        $> git init encryped_repo
        $> cd encryped_repo

Then run `depoly_git_crypt`, and it will guide you to configurate the encryption and decryption settings.

        $> ~/bin/deploy_git_crypt

2. Edit the pattern list file, default is `.gitcrypt`, it works like `.gitignore`. Each line is a pattern to match file names. All matched files will be encrypted before staging(store as git blob files). And they are decrypted when checking out automatically.
The `fnmatch` script is used to match a file name with a file containing glob patterns, there's an example of how to use it:

        \# Encrypt all indexed files
        *
        \# Encrypt files under `passwords` directory
        passwords/\
        \# Just encrypt file `ssh/config`
        ssh/config

3. Commit changes

        $> git commit passwords/ -m "Add password for Facebook"

Then all changes are encrypted and stored as git blobs. If you push the changes to a public remote repository,
others will only see the encrypted version as long as you don't share the salt and key with them.

