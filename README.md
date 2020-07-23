.bash_profile

```
# Git branch in prompt.

parse_git_branch() {

    git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/'

}

export PS1="\u@\h \W\[\033[32m\]\$(parse_git_branch)\[\033[00m\] $ "
```

.zshrc

```
##
#
# Display GIT branch in command prompt.
#
##

# Load version control information
autoload -Uz vcs_info
precmd() { vcs_info }

# Customize the branch information display
zstyle ':vsc_info:git:*' formats '(%b)'

# Customize the prompt display
setopt PROMPT_SUBST
PROMPT = '%n@%m ${PWD/#$HOME/~} %F{green}${vcs_info_msg_0_}%f $ '

```
