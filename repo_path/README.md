# Repo Path

This tox provides a utility method that makes it easier to work with relative paths in TouchDesigner.

## Why

It's best practice to work with relative paths where possible, so your project files will also work on a different system or when it is moved to a different folder. This causes some difficulties when working with external toxes because you'll always have to base your relative paths on the location of the `.tox` file to make it reusable.

Luckily, [as of 2023.10K builds](https://derivative.ca/community-post/word-about-external-files-202310k-builds/68166), TD provides an option to treat paths inside external toxes as relative to the `.tox` file. Though this welcome addition makes toxes way more usable, its implementation has some flaws (try loading a nested external tox using a path relative to the parent tox) and I found myself not trusting TD to always treat relative paths correctly and started following [this suggestion](https://forum.derivative.ca/t/relative-paths-for-external-toxes/7205/5) and writing paths like this: `tdu.expandPath(parent().par.externaltox.val+'/..')+"/my/relative/path"`.

This works great, but it's a bit of a pain to have to write in many places and it requires constant awareness about the operator's location relative to the external tox root ("was it `parent()` or `parent().parent()`?") and now I was wishing for utility method that would make this easier. Which is what this tox provides.

## How it works

This tox provides a `Path` utility method through an extension in its root COMP. By assigning the comp global shortcut (it uses the `REPO` shortcut by default) you can call this `Path` anywhere using an expression like this:

```py
op.REPO.Path("sketch2/images/background.jpg")
```

## Usage

Add the `REPO.tox` to your TD project (doesn't matter where) and make sure the `Global OP Shortcut` field in the `Common` tab of the COMP's parameters has a value in it. By default it will use the `REPO` shortcut.

Then simply use its method in python for parameters that require a filesystem path:

```py
op.REPO.Path("toxes/external.tox")
```

The tox defaults to use the project's current directory (`./`) as the base for the relative paths, but can be configured to use a different root through the custom `Root` parameter.
