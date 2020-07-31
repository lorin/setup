# My setup

Info about my own setup, to help me bootstrap when I get a new laptop.

## Productivity apps

* AntiRSI
* Alfred
* Fantastical
* f.lux
* Haptic touch bar
* iStat Menus
* Karabiner-elements
* Skitch
* TextExpander

### Karabiner-elements

I use Karabiner-elements to remap my Microsoft keyboard's menu button to opt.


## Doc apps

* OmniFocus
* Day One
* Quiver

## CLI apps

* autojump
* ffind
* gdub
* hstr
* httpie
* ripgrep
* [tag](https://github.com/aykamko/tag)

## Dev tools

* Visual Studio Code
* IntelliJ IDEA

## .zshrc customizations

```zsh
alias c="git add . && git commit -m 'checkpoint'"
alias co="code"
alias init="git init && git add ."
alias gitconfig="code ~/.gitconfig"
alias gs="git status"
alias m="make"
alias zshrc="code ~/.zshrc"

# vi bindings
bindkey -v

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
" close fold with space
map <space> zc

" use system clipboard
set clipboard+=unnamed

" case-insensitive search
set ic

" surround
set surround


" actions (see original file for more details)
noremap <C-n> :action GotoNextError<CR>
noremap <C-p> :action GotoPreviousError<CR>
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
