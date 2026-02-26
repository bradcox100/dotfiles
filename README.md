The YouTube video <a href="https://youtu.be/tBoLDpTWVOM?si=TgGgeXHPJv_-fvB3">Git Bare Repository - A Better Way To Manage Dotfiles</a> by <a href="https://www.youtube.com/@DistroTube">DistroTube</a> introduced me to git --bare repositories.
His video sparked excitement on my part. To be able to duplicate my Dot config files from one computer to another, is great. And to save it on git.

This bare repository is based  on the article <a href="https://www.atlassian.com/git/tutorials/dotfiles"> The best way to store your dotfiles: A bare Git repository</a> by Nicola Paolucci.

------------Text version if above link breaks -----------------------------------------------------------
Prior to the installation make sure you have committed the alias to your .bashrc or .zsh:
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'

Now clone your dotfiles into a bare repository in a "dot" folder of your $HOME:
git clone --bare <git-repo-url> $HOME/.cfg

Define the alias in the current shell scope:
alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'

config checkout

The step above might fail with a message like:

error: The following untracked working tree files would be overwritten by checkout:
    .bashrc
    .gitignore
Please move or remove them before you can switch branches.
Aborting

Re-run the check out if you had problems:
config checkout

Set the flag showUntrackedFiles to no on this specific (local) repository:
config config --local status.showUntrackedFiles no
---------------------------------------------------------------------------------------------------

