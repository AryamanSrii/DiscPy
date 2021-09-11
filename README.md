# DiscPy

[![Discord server invite](https://discord.com/api/guilds/884072759540461568/embed.png)](https://discord.gg/z5VQEjskEs) [![PyPI version info](https://img.shields.io/pypi/v/discpy.svg)](https://pypi.python.org/pypi/discpy) [![PyPI supported Python versions](https://img.shields.io/pypi/pyversions/discpy.svg)](https://pypi.python.org/pypi/discpy) [![Documentation Status](https://readthedocs.org/projects/discpy/badge/?version=latest)](https://discpy.readthedocs.io/en/latest/?badge=latest)

A modern, easy to use, feature-rich, and async ready API wrapper for
Discord written in Python, based on `discord.py`.


## Key Features

-   Modern Pythonic API using `async` and `await`.
-   Proper rate limit handling.
-   Optimised in both speed and memory.

## Installing

**Python 3.8 or higher is required**

To install the library without full voice support, you can just run the
following command:

```sh
# Linux/macOS
python3 -m pip install -U discpy

# Windows
py -3 -m pip install -U discpy
```

Otherwise to get voice support you should run the following command:

```sh
# Linux/macOS
python3 -m pip install -U "discpy[voice]"

# Windows
py -3 -m pip install -U discpy[voice]
```

To install the development version, do the following:

```sh
$ git clone https://github.com/DiscPy/DiscPy
$ cd DiscPy
$ python3 -m pip install -U .[voice]
```

## Optional Packages

-   [PyNaCl](https://pypi.org/project/PyNaCl/) (for voice support)

Please note that on Linux installing voice you must install the
following packages via your favourite package manager (e.g. `apt`,
`dnf`, etc) before running the above commands:

-   libffi-dev (or `libffi-devel` on some systems)
-   python-dev (e.g. `python3.6-dev` for Python 3.6)

## Quick Example

### Client Example

```py
import discpy

class MyClient(discpy.Client):
    async def on_ready(self):
        print('Logged on as', self.user)

    async def on_message(self, message):
        # don't respond to ourselves
        if message.author == self.user:
            return

        if message.content == 'ping':
            await message.channel.send('pong')

client = MyClient()
client.run('token')
```

### Bot Example

```py
import discpy
from discpy.ext import commands

bot = commands.Bot(command_prefix='>')

@bot.command()
async def ping(ctx):
    await ctx.send('pong')

bot.run('token')
```

You can find more examples in the `examples` directory.

## Links

-   [Documentation](https://discpy.readthedocs.io/en/latest/index.html)
-   [Issue Tracker](https://github.com/DiscPy/DiscPy/issues)
-   [Support Server](https://discord.gg/z5VQEjskEs)

## License

Copyright (c) 2021 The DiscPy Developers  
Copyright (c) 2015-2021 Rapptz



