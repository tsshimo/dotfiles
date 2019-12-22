DOTFILES_EXCLUDES := .DS_Store .git
DOTFILES_TARGET := $(wildcard .??*)
DOTFILES_FILES := $(filter-out $(DOTFILES_EXCLUDES), $(DOTFILES_TARGET))
XDG_CONFIG_TARGET := $(wildcard ./XDG_CONFIG_HOME/*/)
CONFIG_DIR := $(HOME)/.config/

deploy: init
	@$(foreach file, $(DOTFILES_FILES), ln -sfnv $(abspath $(file)) $(HOME)/$(file);)
	@$(foreach dir, $(XDG_CONFIG_TARGET), ln -sfnv $(abspath $(dir)) $(CONFIG_DIR);)

init: $(CONFIG_DIR)
	mkdir -p $@

update: ## Fetch changes for this repo
	git pull origin master

