# My setup

Info about my own setup, to help me bootstrap when I get a new laptop.

## Productivity apps

* AntiRSI
* Alfred
* Default Folder X
* Fantastical
* f.lux
* Haptic touch bar
* iStat Menus
* [Kaleidoscope](https://www.kaleidoscopeapp.com/)
* Karabiner-elements
* [Muzzle](https://muzzleapp.com/)
* Skitch
* TextExpander
* ToothFairy
* [Witch](https://manytricks.com/witch/)


### Karabiner-elements

I use Karabiner-elements to remap my Microsoft keyboard's menu button to opt.


## Doc apps
* Bear
* GoodNotes
* OmniFocus
* Day One
* Quiver

## CLI apps

* autojump
* bat
* exa
* ffind
* fzf
* gdub
* hstr
* httpie
* ripgrep
* [scmpuff](https://github.com/mroth/scmpuff)
* [tag](https://github.com/aykamko/tag)

## Dev tools

* Visual Studio Code
* IntelliJ IDEA

## .zshrc customizations

```zsh
# Don't do the magic URL escape thing
DISABLE_MAGIC_FUNCTIONS=true

# Show only the name of the directory in the title
ZSH_THEME_TERM_TITLE_IDLE="%~"

alias agt='ag --ignore test'
alias c="git add . && git commit -m 'checkpoint'"
alias co="code"
alias dir="pwd | pbcopy"
alias init="git init && git add ."
alias gdt="git difftool"
alias gitconfig="code ~/.gitconfig"
alias gs="git status"
alias jump='cd `greadlink -f .`'
alias m="make"
alias pf="open -a 'Path Finder'"
alias pull="git checkout master && git pull --prune"
alias zshrc="code ~/.zshrc"

export EDITOR='code'
export HSTR_CONFIG=hicolor

# vi bindings with c-a and c-e emacs-style
bindkey -v
bindkey "^A" vi-beginning-of-line
bindkey "^E" vi-end-of-line

plugins=(vi-mode zsh-autosuggestions)


# Render a markdown file as html in the browser
# do a "brew install browser" to get the browser app so you can pipe html to
# your browser
function html {
    CSS="https://rawgit.com/lorin/macdown/master/MacDown/Resources/Styles/GitHub2.css"
    if [ $#@ -eq 0 ]; then
        if [[ -a README.md ]]; then
            FNAME=README.md
        else
            FNAME=(*.md)
        fi
    else
        FNAME="$1"
    fi
    pandoc -c $CSS $FNAME | browser
}

# https://github.com/aykamko/tag
if (( $+commands[tag] )); then
  export TAG_SEARCH_PROG=rg 
  export TAG_CMD_FMT_STRING="code --goto {{.Filename}}:{{.LineNumber}}:{{.ColumnNumber}}"
  tag() { command tag "$@"; source ${TAG_ALIAS_FILE:-/tmp/tag_aliases} 2>/dev/null }
  alias ag=tag
  alias rg=tag
fi

[ -f /usr/local/etc/profile.d/autojump.sh ] && . /usr/local/etc/profile.d/autojump.sh
```


## Visual Studio Code

### System clipboard

```
cmd shift p > Preferences: Open User Settings > Vim : Use system clipboard
```

###  .ideavimrc

```
" spacemacs behavior
" https://stackoverflow.com/a/43072912
imap fd <Esc>
set timeoutlen=1000
"
" Cycle through buffers
map <Tab> gt
map <S-Tab> gT

" close fold with space
map <space> zc


" use system clipboard
set clipboard+=unnamed

" case-insensitive search
set ic

" surround
set surround

" To see the names of all of the commands, type the following in IDEA
" :actionlist
" https://github.com/JetBrains/ideavim#executing-ide-actions
noremap <C-r> :action Run<CR>
noremap <C-b> :action ToggleLineBreakpoint<CR>
noremap <C-n> :action GotoNextError<CR>
noremap <C-p> :action GotoPreviousError<CR>

let mapleader = ","
noremap <leader>b :action CloseActiveTab<CR>
noremap <leader>d :action CopyPaths<CR>
noremap <leader>D :action CopyPaths<CR>
```


### Snippets

Preferences: Configure User Snippets > ruby.json (Ruby)


```json
{
	"Dash entry": {
		"prefix": ["entry"],
		"body": [
			"entry do",
			"\tname '$1'",
			"\tnotes <<-'END'",
			"\t```",
			"\t$0",
			"\t```",
			"\tEND",
			"end"
		],
	},
	"Dash category": {
		"prefix": "category",
		"body": [
			"category do",
			"\tid '$1'",
			"\t$0",
			"end"
		]
	}
}
```

## Dash

* [cheatset](https://github.com/Kapeli/cheatset)
* [My personal cheat sheets](https://github.com/lorin/cheat-sheets)

## Alfred

* [Custom Alfred iTerm Scripts](https://github.com/vitorgalvao/custom-alfred-iterm-scripts)
