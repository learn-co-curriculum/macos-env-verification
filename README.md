# Verify and Troubleshoot your macOS Environment Setup 

## Action Item

1. Open your "Terminal" application using "Spotlight Search"
2. Type `curl -so- https://raw.githubusercontent.com/learn-co-curriculum/flatiron-manual-setup-validator/master/mac-manual-setup-validator.sh | zsh 2> /dev/null`

## Check Your Work

If all checks pass, you have completed your environment setup and are ready to move on!

If something does not pass, that is okay. Revisit the installation instructions for the
item that did not pass. If you are able to run the commands listed in
the **Check Your Work** section for that item, this may just be an issue with the validator.

## Troubleshooting

### Fixing NVM and RVM Dotfile Issues for MacOS

If you are having trouble getting RVM, Ruby, NVM, or Node to work, you may have an issue with your `.zshrc` file. To fix, we need to run two commands.

The first command makes a backup of your current `.zshrc` file:

```sh
mv ~/.zshrc{,.bak}
```

The second command replaces the contents of your `.zshrc` file with a default dot file:

```sh
curl -sSL https://raw.githubusercontent.com/flatiron-school/dotfiles/master/.zshrc > ~/.zshrc
```

Close and reopen your terminal. With a new `.zshrc` file, we can now test out each tool.

### Verify RVM is Installed

To confirm that RVM is working, run:

```sh
rvm
```

If you see a long message ending in `“For additional documentation please visit https://rvm.io”`, RVM is installed.

> If the command `rvm` is not recognized, do the following in your terminal:
>
> 1. Type `brew install gmp` and press `<Enter>`
> 2. Type `brew install gnupg` and press `<Enter>`
> 3. Type `curl -sSL https://rvm.io/mpapis.asc | gpg --import -` and press `<Enter>`
> 4. Type `curl -sSL https://rvm.io/pkuczynski.asc | gpg --import -` and press `<Enter>`
> 5. Type `\curl -sSL https://get.rvm.io | bash` and press `<Enter>`
> 6. Close the "Terminal" application
> 7. Reopen the "Terminal" application

### Verify Ruby is Installed

To confirm Ruby is installed, run:

```sh
rvm list
```

If you see `=* ruby-2.6.1`, Ruby is installed and 2.6.1 set as the default version and you are all set for Ruby.

> If you do not see `ruby-2.6.1` at all, install it with the following command:
>
> ```sh
> rvm install ruby-2.6.1
> ```

> If `ruby-2.6.1` is listed, but is not preceded by `=*`, make it the default version by running:
>
> ```sh
> rvm use 2.6.1 --default
> ```

### Verify NVM is installed

To confirm NVM is installed, run:

```sh
nvm
```

If you see a message ending with `“Note: to remove, delete, or uninstall nvm…”`, NVM is installed. 

> If the `nvm` command is not recognized or you see an error `complete:13: command not found: compdef`, run the following command:
>
> ```sh
> curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh | bash
> ```

### Verify Node is Installed

To confirm Node is installed, run:

```sh
nvm list
```

If you see a message starting with “-> v14.13.0” (or any number higher than this), a version of Node is installed that will work for this course.

> If you don't see this number, install the newest version of Node:
>
> ```sh
> nvm install node
> ```

<!-- ## Troubleshooting

Below are some options to try for specific issues.

### RVM Is Producing Errors or Warnings

1. Close your terminal, reopen it, and try the `rvm list` command.

2. If you see a warning regarding the `PATH`, try running the following
   first:

   ```sh
   rvm use 2.6.1
   rvm --default use 2.6.1
   ```

   Close and reopen the terminal again, and rerun `rvm list`.

3. If RVM is not found when you run `rvm list`, try reinstalling RVM:

    ```sh
    curl -sSL https://get.rvm.io | bash -s stable --ruby --auto-dotfiles
    ```

    You may get an error regarding keys with further
    commands to try, including the following:

    ```sh
    gpg --keyserver hkp://pool.sks-keyservers.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3 7D2BAF1CF37B13E2069D6956105BD0E739499BDB

    or if it fails:

    command curl -sSL https://rvm.io/mpapis.asc | gpg --import -
    command curl -sSL https://rvm.io/pkuczynski.asc | gpg --import -
    ```

   Try each of these, followed by the previous `curl` command to install RVM.

4. If RVM is found but continues to produce errors, try uninstalling with:

   ```sh
   rvm implode
   ```

   This will remove RVM entirely. Follow the instructions in Step 3 to reinstall RVM.

### `learn whoami` Command Not Found / `learn` Produces `oj.bundle` Error

1. Close your terminal window, reopen it, and try the `learn whoami` command
   again.

2. Run the command `rvm list`. If RVM is not found, follow the steps in the
   previous troubleshooting section on installing RVM. If you see a warning
   regarding `PATH`, try running the following first:

   ```sh
   rvm use 2.6.1
   rvm --default use 2.6.1
   ```

   Then reinstall the Learn gem and test it again with:

   ```sh
   gem install learn-co
   learn whoami
   ```

3. If the `learn` command continues to fail, but RVM is working fine, try
   reinstalling RVM by first using the following command:

   ```sh
   rvm implode
   ```

   Then rerunning the RVM install script:

   ```sh
   curl -sSL https://get.rvm.io | bash -s stable --ruby --auto-dotfiles
   ```

   Once RVM is installed, try reinstalling and testing the `learn-co` gem.

4. If you are still unable to run `learn whoami`, try the following:

   ```sh
   bundle clean --force
   gem install learn-co
   gem install bundler
   ```

   This will clear out any gems that have already been installed. At the moment,
   you will only need the `learn-co` and `bundler` gems, so this reinstalls
   them.

### `learn` Commands Produce `psych` Gem Errors

This error is typically due to issues in the `~/.learn-config` file. 

1.  Run `code ~/.learn-config`. This file should only have three lines in it, 
    similar to the example below:

    ```sh
    ---
    :learn_directory: "/Users/< username >/Flatiron/code"
    :editor: code
    ```

2.  Check for any typos or extra content. Make sure the `:learn_directory` path
    is valid and has your computer's username after `/Users/`. You can confirm this
    name by running `echo $HOME`. 

3.  Save the `.learn-config` file and try running `learn whoami`.  -->
