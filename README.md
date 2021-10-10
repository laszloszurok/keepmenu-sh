# keepmenu-sh

## Description
A very simple dmenu wrapper script that lists entries from a keepassxc database and copies the picked password to the clipboard.

## Limitations
Right now the usage is very limited. In order to use this script, your database have to be set to use only a key file to unlock and no password. This is because `keepassxc-cli` can't read a password from stdin, so the script can't promt the user to enter their password. However a key file can be passed to `keepassxc-cli` along with the `--no-password` flag. Keep in mind that using no password on the database is not considered secure. If an attacker has access to your db and key, they need nothing else to access your passwords.

## Install
```
git clone https://github.com/laszloszurok/keepmenu-sh.git
cd keepmenu-sh
sudo make install
```
This will install the script to `/usr/local/bin`.

## Usage
Run the script to generate a template config file in `$XDG_CONFIG_HOME/keepmenu-sh/config` (`~/.config/` by default). Edit the file and provide the absolute path to your database and key file. `$HOME` and `~` won't work, you need to type the full path. You can pass flags to dmenu in the config file. Example:
```
db_path=/home/user/passwords.kdbx
key_path=/home/user/key
dmenu_flags=-c -l 20
```
