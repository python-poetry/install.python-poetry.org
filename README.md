# Python Poetry Installer
This repository contains Poetry's official installation script, installer source and
related hosting configuration.

The script is hosted on [Vercel](https://vercel.com/) and made available at
https://install.python-poetry.org/.

## Usage

Poetry provides a custom installer that will install `poetry` isolated
from the rest of your system.

### osx / linux / bashonwindows install instructions
```bash
curl -sSL https://install.python-poetry.org | python -
```
### windows powershell install instructions
```powershell
(Invoke-WebRequest -Uri https://install.python-poetry.org -UseBasicParsing).Content | python -
```

**Warning**: The previous `get-poetry.py` installer is now deprecated, if you are currently using it
you should migrate to the new, supported, `install-poetry.py` installer.

The installer installs the `poetry` tool to Poetry's `bin` directory. This location depends on your system:

- `$HOME/.local/bin` for Unix
- `%APPDATA%\Python\Scripts` on Windows

If this directory is not on your `PATH`, you will need to add it manually
if you want to invoke Poetry with simply `poetry`.

Alternatively, you can use the full path to `poetry` to use it.

Once Poetry is installed you can execute the following:

```bash
poetry --version
```

If you see something like `Poetry (version 1.2.0)` then you are ready to use Poetry.
If you decide Poetry isn't your thing, you can completely remove it from your system
by running the installer again with the `--uninstall` option or by setting
the `POETRY_UNINSTALL` environment variable before executing the installer.

```bash
python install-poetry.py --uninstall
POETRY_UNINSTALL=1 python install-poetry.py
```

By default, Poetry is installed into the user's platform-specific home directory.
If you wish to change this, you may define the `POETRY_HOME` environment variable:

```bash
POETRY_HOME=/etc/poetry python install-poetry.py
```

If you want to install prerelease versions, you can do so by passing `--preview` option to `install-poetry.py`
or by using the `POETRY_PREVIEW` environment variable:

```bash
python install-poetry.py --preview
POETRY_PREVIEW=1 python install-poetry.py
```

Similarly, if you want to install a specific version, you can use `--version` option or the `POETRY_VERSION`
environment variable:

```bash
python install-poetry.py --version 1.2.0
POETRY_VERSION=1.2.0 python install-poetry.py
```

You can also install Poetry for a `git` repository by using the `--git` option:

```bash
python install-poetry.py --git https://github.com/python-poetry/poetry.git@master
````

**Note**: Note that the installer does not support Python < 3.6.
