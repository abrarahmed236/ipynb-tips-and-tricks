# IPYNB Tips and Tricks

### Strip output from ipython notebooks for git

When using ipython notebooks, usually the output is saved as part of the
notebook. This output is desirable almost always except for when we want to use
git for version control. In this one case the output is too large and wasteful
of resources.

To strip the output of ipynb files when tracking changes with git do the
following:

#### Install nbstripout

```bash
pip install nbstripout nbconvert
```

#### Setup nbstripout for a git repo

```bash
# initialize the repo
git init

# setup the git filter
nbstripout --install

# add relevant files
git add .

# check if the notebook is stripped
git diff --cached
```

Subsequent git operations will have the output stripped for ipynb files.

> Care is recommended if using virtual environments. Either install nbstripout
> in the global environment or always use git from within the environment.
> _(Needs confirmation)_

#### Other

If you want to set up the git filter in your global `~/.gitconfig`

```bash
nbstripout --install --global
```

Similarly if you want to set up the git filter in your system-wide
`$(prefix)/etc/gitconfig`

```bash
sudo nbstripout --install --system
```

To remove the git filter and attributes:

```bash
nbstripout --uninstall
# or
nbstripout --uninstall --global
# or
sudo nbstripout --uninstall --system
```
