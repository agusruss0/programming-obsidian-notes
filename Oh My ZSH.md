
---
## Archivo de configuración

en el archivo ```.zshrc``` se puede configurar el theme y los plugins

```bash
# If you come from bash you might have to change your $PATH.

# export PATH=$HOME/bin:/usr/local/bin:$PATH

  

# Path to your oh-my-zsh installation.

export ZSH="$HOME/.oh-my-zsh"

  

# Set name of the theme to load --- if set to "random", it will

# load a random theme each time oh-my-zsh is loaded, in which case,

# to know which specific one was loaded, run: echo $RANDOM_THEME

# See https://github.com/ohmyzsh/ohmyzsh/wiki/Themes

ZSH_THEME="robbyrussell"

  

# Set list of themes to pick from when loading at random

# Setting this variable when ZSH_THEME=random will cause zsh to load

# a theme from this variable instead of looking in $ZSH/themes/

# If set to an empty array, this variable will have no effect.

# ZSH_THEME_RANDOM_CANDIDATES=( "robbyrussell" "agnoster" )

  

# Uncomment the following line to use case-sensitive completion.

# CASE_SENSITIVE="true"

  

# Uncomment the following line to use hyphen-insensitive completion.

# Case-sensitive completion must be off. _ and - will be interchangeable.

# HYPHEN_INSENSITIVE="true"

  

# Uncomment one of the following lines to change the auto-update behavior

# zstyle ':omz:update' mode disabled  # disable automatic updates

# zstyle ':omz:update' mode auto      # update automatically without asking

# zstyle ':omz:update' mode reminder  # just remind me to update when it's time

  

# Uncomment the following line to change how often to auto-update (in days).

# zstyle ':omz:update' frequency 13

  

# Uncomment the following line if pasting URLs and other text is messed up.

# DISABLE_MAGIC_FUNCTIONS="true"

  

# Uncomment the following line to disable colors in ls.

# DISABLE_LS_COLORS="true"

  

# Uncomment the following line to disable auto-setting terminal title.

# DISABLE_AUTO_TITLE="true"

  

# Uncomment the following line to enable command auto-correction.

# ENABLE_CORRECTION="true"

  

# Uncomment the following line to display red dots whilst waiting for completion.

# You can also set it to another string to have that shown instead of the default red dots.

# e.g. COMPLETION_WAITING_DOTS="%F{yellow}waiting...%f"

# Caution: this setting can cause issues with multiline prompts in zsh < 5.7.1 (see #5765)

# COMPLETION_WAITING_DOTS="true"

  

# Uncomment the following line if you want to disable marking untracked files

# under VCS as dirty. This makes repository status check for large repositories

# much, much faster.

# DISABLE_UNTRACKED_FILES_DIRTY="true"

  

# Uncomment the following line if you want to change the command execution time

# stamp shown in the history command output.

# You can set one of the optional three formats:

# "mm/dd/yyyy"|"dd.mm.yyyy"|"yyyy-mm-dd"

# or set a custom format using the strftime function format specifications,

# see 'man strftime' for details.

# HIST_STAMPS="mm/dd/yyyy"

  

# Would you like to use another custom folder than $ZSH/custom?

# ZSH_CUSTOM=/path/to/new-custom-folder

  

# Which plugins would you like to load?

# Standard plugins can be found in $ZSH/plugins/

# Custom plugins may be added to $ZSH_CUSTOM/plugins/

# Example format: plugins=(rails git textmate ruby lighthouse)

# Add wisely, as too many plugins slow down shell startup.

plugins=(git zsh-syntax-highlighting zsh-autosuggestions zsh-completions fzf)

  

source $ZSH/oh-my-zsh.sh

  

# User configuration

  

#MyPy configuration

export PATH="$HOME/.local/bin:$PATH"

  
  

# FZF configuration

export FZF_BASE="$HOME/.fzf"

export FZF_DEFAULT_OPTS="--multi \

--height 100% \

--layout=reverse \

--border \

--info=default \

--prompt='~' \

--pointer='➜' \

--marker='✓'"

  

export FZF_ALT_C_OPTS="--preview 'echo \"Directory Tree:\"; tree -C {} | head -n 50' --preview-window 50%:right:border:wrap"

  

export FZF_CTRL_T_COMMAND='(cd $HOME && find . -type f ! -path "/." ! -path "/.git/" ! -path "/.venv/" ! -path "/venv/" ! -path "/snap/"  -print | sed "s|^./||")'

# export FZF_CTRL_T_OPTS="--preview '[ -f {} ] && bat --style=numbers --color=always {} | head -500' --preview-window right:50%:wrap --height 100% --layout=reverse --border --info=default --prompt='FZF-CTRL-T>' --pointer='➜' --marker='✓'"

  
  

# export MANPATH="/usr/local/man:$MANPATH"

  

# You may need to manually set your language environment

# export LANG=en_US.UTF-8

  

# Preferred editor for local and remote sessions

# if [[ -n $SSH_CONNECTION ]]; then

#   export EDITOR='vim'

# else

#   export EDITOR='mvim'

# fi

  

# Compilation flags

# export ARCHFLAGS="-arch x86_64"

  

# Set personal aliases, overriding those provided by oh-my-zsh libs,

# plugins, and themes. Aliases can be placed here, though oh-my-zsh

# users are encouraged to define aliases within the ZSH_CUSTOM folder.

# For a full list of active aliases, run `alias`.

#

# Example aliases

alias zshconfig="code ~/.zshrc"

# alias ohmyzsh="mate ~/.oh-my-zsh"

alias jupyter-lab="~/.local/bin/jupyter-lab --no-browser"

alias uvi-app="uvicorn app.main:app --reload"

alias redis-start="sudo service redis-server start"

alias redis-stop="sudo service redis-server stop"

alias py-venv="python3 -m venv .venv"

alias venv-activate="source .venv/bin/activate"

alias pg-start="sudo service postgresql start"

alias pg-stop="sudo service postgresql stop"

alias pg="sudo -u postgres psql"

alias cls="clear"

alias docker-up="docker compose -f docker-compose.dev.yml up"

alias docker-build="docker compose -f docker-compose.dev.yml up --build"

alias docker-down="docker compose -f docker-compose.dev.yml down"

alias docker-d="docker compose -f docker-compose.dev.yml up -d"

alias alembic-rev="alembic revision --autogenerate -m"

alias alembic-up="alembic upgrade head"
```

---
## Fuzzy Finder
para instalar fuzzy finder:
1. Correr el comando ```sudo apt install fzf```
2. Correr el comando ```sudo apt-get install ripgrep```
3. Descargar [bat-musl_0.24.0_amd64.deb](https://github.com/sharkdp/bat/releases)en Ubuntu
4. Correr el comando ```sudo dpkg -i bat-musl_0.24.0_amd64.deb```
5. Chequear ```fzf --version rg --version bat --version```
6. Correr ```sudo apt install tree```
7. Instalar en vscode FindItFaster 