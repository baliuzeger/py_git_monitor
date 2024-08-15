# Use Case

This project is intended to improve datascience workflows. You may want to do these simultaneously:
1. Developing a package (the *package project*), possibly a machine learning model or a data pipeline.
2. Perform some experiments in another project (the *experiment project*)  by such package by running a jupyter notebook or a script.
3. Log the git status of the package for reproducibiliy.

`git-monitor` help you for to conviniently log the git status.

If we don't want the notebooks to polute the *package project*, we have to separate it from the *package project*, then we cannot track everying directly in a git repo. This problem is what `git-monitor` built for.

# How to

1. Install `git-monitor` into the environment of your *package project*.
2. Make a `.git_monitor` file in the *experiment project* or make the setting by environment variables (`git-monitor` uses `python-dotenv`):
```
<pkg-nm>=<pkg-path>
```
3. In the topmost `__init__.py`, add the lines:
```python
import git_monitor
git_monitor.Monitor.by_env("<pkg-nm>")
```

Then everytime you `import` or `reload` the *package project*, `git-monitor` will print the git status, including current branch, commit hash, untracked files and modified files.