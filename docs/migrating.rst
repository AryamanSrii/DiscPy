.. currentmodule:: discpy

.. _migrating_to_discpy:

Migrating to DiscPy
======================

Migrating to this library is fairly easy, with all the ``discord`` references being changed to ``discpy``.

For example, the following code in ``discord.py``:

.. code:: py

    import discord

    class MyClient(discord.Client):
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

would look like this in ``discpy``:

.. code:: py

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