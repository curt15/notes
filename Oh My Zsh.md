Links: [[PROGRAMMING]] - [[TECHNOLOGY]]
Rel: [[macos]]
Ref: https://ohmyz.sh/; https://github.com/ohmyzsh/ohmyzsh/wiki
Tags: #public 

--- 
install:
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

```apt install zsh```

```bash
Cloning Oh My Zsh...
Cloning into '/Users/curt/.oh-my-zsh'...
remote: Enumerating objects: 1194, done.
remote: Counting objects: 100% (1194/1194), done.
remote: Compressing objects: 100% (1162/1162), done.
remote: Total 1194 (delta 20), reused 1131 (delta 16), pack-reused 0
Receiving objects: 100% (1194/1194), 827.50 KiB | 6.00 MiB/s, done.
Resolving deltas: 100% (20/20), done.

Looking for an existing zsh config...
Found ~/.zshrc. Backing up to /Users/curt/.zshrc.pre-oh-my-zsh
Using the Oh My Zsh template file and adding it to ~/.zshrc.

         __                                     __
  ____  / /_     ____ ___  __  __   ____  _____/ /_
 / __ \/ __ \   / __ `__ \/ / / /  /_  / / ___/ __ \
/ /_/ / / / /  / / / / / / /_/ /    / /_(__  ) / / /
\____/_/ /_/  /_/ /_/ /_/\__, /    /___/____/_/ /_/
                        /____/                       ....is now installed!


Before you scream Oh My Zsh! please look over the ~/.zshrc file to select plugins, themes, and options.

• Follow us on Twitter: https://twitter.com/ohmyzsh
• Join our Discord server: https://discord.gg/ohmyzsh
• Get stickers, shirts, coffee mugs and other swag: https://shop.planetargon.com/collections/oh-my-zsh

[oh-my-zsh] Insecure completion-dependent directories detected:
drwxrwxr-x  3 curt  admin   96 Mar  7  2020 /usr/local/share/zsh
drwxrwxr-x  7 curt  admin  224 May 30  2020 /usr/local/share/zsh/site-functions

[oh-my-zsh] For safety, we will not load completions from these directories until
[oh-my-zsh] you fix their permissions and ownership and restart zsh.
[oh-my-zsh] See the above list for directories with group or other writability.

[oh-my-zsh] To fix your permissions you can do so by disabling
[oh-my-zsh] the write permission of "group" and "others" and making sure that the
[oh-my-zsh] owner of these directories is either root or your current user.
[oh-my-zsh] The following command may help:
[oh-my-zsh]     compaudit | xargs chmod g-w,o-w

[oh-my-zsh] If the above didn't help or you want to skip the verification of
[oh-my-zsh] insecure directories you can set the variable ZSH_DISABLE_COMPFIX to
[oh-my-zsh] "true" before oh-my-zsh is sourced in your zshrc file.

```

uninstall:
```bash
$ sudo chmod 777 ~/.oh-my-zsh/tools/uninstall.sh
$ ~/.oh-my-zsh/tools/uninstall.sh
```