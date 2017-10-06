Ubuntu to MacOS
----

MacOS Sierra 10.12.6 Macbook Pro ( Ratina )

Version History
10.10 Yosemite
10.11 EI Captian
10.12 Sierra


###keyboard shortcuts
keybaord symbol list can be visible at (  icon --> System Preferences --> Keyboard > Modifier Keys)

⌘ = Command
⇧ = Shift
⌥ = Option (a.k.a. Alt)
⌃ = Ctrl
⎋ = Esc
↩︎ = Return
⌫ = Delete (a.k.a. Backspace)

- `⌘ + ⇧ + H`  = Home

- `⌘ + ⇧ + D`  = Desktop

- `⌘ + ⇧ + A`  = Application

- `⌘ + ⇧ + U` = Utilities

- `⌘ + ⇧ + .` = Toggle Hidden files within a folder

- `⌘ + ⌃ + T` => Add folder to sidebar (bookmark)

- `⌘ + ⌃ + F` => Maximize current active window

###Findings

1. You can not create new file from context menu but can create new folder only. use `touch filename` from terminal

2. No utility to lock the monitor.
    alternative:
    	a. Navigate to  icon --> System Preferences --> Security & Privacy --> General --> Check Require Password *immediately* after sleep or screen saver starts
    	b.  hit *shift + control + power* (`⇧ + ^ + Power`) and hold down for two seconds, revoke by spacebar.

3. No way to see hidden files in a folder. found keyboard shortcut lately  and that is `⌘ + ⇧ + .` ,  alternatively open terminal and run following command

    `defaults write com.apple.Finder AppleShowAllFiles true` and than `killall Finder`

4. No way to see file system. alternatively go to Finder , alternatively `⌘ + ⇧ + H`  => open Home folder ( in Finder ) then `⌘ + ⇧ + G` ==> write location name

5. *Open in Terminal* directly within folder ifrom context menu is ?missing, alternatively

     icon --> System Preferences --> Keyboard --> Shortcuts --> Services --> Enable "New Terminal at Folder"

        How to check this : suppose we have to open /opt/alpha/beta folder in terminal. navigate to the parent folder(alpha), select the relevant folder (beta), right click on it, open context menu --> Services --> Open Folder in Terminal

5. install `brew` in place of `apt-get`, run below command in terminal; Refrence http://brew.sh

    `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`


6. Unable to keep project open in Sublime-text-3 while we close all the files. alternative : use `⇧ + Q` to close sublime completely.

8. set title of tab in terminal , keyboard shortcut `⌘ + i` , pop-up opens , write tab or window title ; after rename press `⌘ + i` ( or Esc ⎋ ) again

9. no window maximize, if you click on maximize, it will span over the screen and hide the menu. alternatively use double tab on window will adjust according to screen width


10. Remove entry from context menu

   icon --> System Preferences --> Keyboard --> Shortcuts --> Services > text > uncheck the un necesray item from context menu such as "Add to iTunes as a Spken Track"

11. enable mouse scroll reverse.

   icon --> System Preferences --> Mouse --> Uncheck Scoll Direction : Natural ( located on top )

12. set function keys ( F1 F2 ) as normal

   icon > System Prefrences ( Apple icon) > Keyboards > (last option) check F1.F2, etc.. keys as standard keys

11. Remove Siri

   icon --> System Preferences --> Siri --> Uncheck Enable Siri on right side panel

12. delete button is backspace and if you want to remove forward use `fn + Delete`

13. remove Notification of stocks

   icon --> System Preferences --> Extensions --> Today --> uncheck Stock

14. Rename a file : select File and Press Enter (return)

15. make link for sublime so that it can be opened from terminal by hit `subl`

`sudo ln -s "/Applications/Sublime Text.app/Contents/SharedSupport/bin/subl" /usr/local/bin/subl`

16. colorful terminal and git branch name in terminal and git autocomplete feature.

first install `curl https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash -o ~/.git-completion.bash`

add following in **~/.bash_profile** ( create if not exist)


```
# Git branch in prompt
parse_git_branch() {
    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'
}

RED="\[\033[0;31m\]"
YELLOW="\[\033[1;33m\]"
GREEN="\[\033[0;32m\]"
BLUE="\[\033[1;34m\]"
LIGHT_RED="\[\033[1;31m\]"
LIGHT_GREEN="\[\033[1;32m\]"
WHITE="\[\033[1;37m\]"
LIGHT_GRAY="\[\033[0;37m\]"
COLOR_NONE="\[\e[0m\]"

export PS1="${GREEN}\u@${LIGHT_GRAY}\h:${LIGHT_RED}\w${LIGHT_GREEN}\$(parse_git_branch)${BLUE} $ "

if [ -f ~/.git-completion.bash ]; then
  . ~/.git-completion.bash
fi

export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad
alias ls='ls -GFh'
```



> `⌘ + Option + J` => chrome developer tools


> Hit `subl .` from the location of peoject folder to open project in sublime.


> You can not cut files from a folder !!

> When you click on a zip file and select Open; it will extract the zip into same folder.


- install XtraFinder for adding copy move and other feature in folder/file context menu

- `brew install coreutils`

- to rid out of blurry text on Secodary Desktop change settings

     --> System Preferences --> General --> Select “Use LCD font smoothing when available” (at the bottom of the preference pane).


###mysql

download and install ; it will set default password which will be displayed after succesfull installtion completion; note down
now first make symbolic link for mysql to run from terminal

```
echo 'export PATH="$PATH:/usr/local/mysql/bin"' >> ~/.profile
source ~/.profile
```

$: `mysql -u root -p`

change default password

mysql>

`SET PASSWORD FOR 'root'@'localhost' = PASSWORD('new_password');`
Query OK, 0 rows affected, 1 warning

`exit;`

now you can access with your password

. mysql start stop restart

` sudo /usr/local/mysql/support-files/mysql.server start/stop/restart`

Or you can set alias to mysql
`alias mysql=/usr/local/mysql/bin/mysql`
and then run below query
$: `mysql -u root -p`
Enter Password:
