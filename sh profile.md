Links: [[PROGRAMMING]]

--- 

```bash
export CLICOLOR=1
export LSCOLORS=GxFxCxDxBxegedabagaced

alias ls="ls -G"
alias ll="ls -lGa"
alias icloud="cd $HOME/Library/Mobile\ Documents/com\~apple\~CloudDocs/Stuff"
alias onotes="cd $HOME/Library/Mobile\ Documents/com\~apple\~CloudDocs/Stuff/onotes"

alias nano="/usr/local/Cellar/nano/5.8/bin/nano"

alias gs="git status"
alias activate=". ~/prog/.envs/venv/bin/activate"

alias editprofile="nano ~/.zshrc"
alias reloadprofile="source ~/.zshrc"

alias excel="open -a /Applications/Microsoft\ Excel.app"
alias octave="open -a /Applications/Octave-cli.app"
#alias subl="open -a /Applications/Sublime\ Text.app/"
alias code="open -a /Applications/Visual\ Studio\ Code.app"


activate # <- enter every new shell within the main python env


subl() {
	p=${1:-.}
	open -a /Applications/Sublime\ Text.app/ $1
}

touchr() {

## new rft pre-embedded stuff] ##
# '{\rtf1\ansi\ansicpg1252\cocoartf1671\cocoasubrtf400'
# '{\fonttbl}'
# '{\colortbl;\red255\green255\blue255;}'
# '{\*\expandedcolortbl;;}'
# '\margl1440\margr1440\vieww10800\viewh8400\viewkind0'
# '}'
        rtf_input='{\rtf1\ansi\ansicpg1252\cocoartf1671\cocoasubrtf400\n{\fontt$

        if [[ $1 =~ \.rtf$ ]]; then
                echo -n $rtf_input > "$1"
        else
                echo -n $rtf_input > "$1.rtf"
        fi
}
```
