.. currentmodule:: discpy

API Reference
===============

The following section outlines the API of ``discpy``'s command extension module.

.. _ext_commands_api_bot:

Bots
------

Bot
~~~~

.. attributetable:: discpy.ext.commands.Bot

.. autoclass:: discpy.ext.commands.Bot
    :members:
    :inherited-members:
    :exclude-members: after_invoke, before_invoke, check, check_once, command, event, group, listen

    .. automethod:: Bot.after_invoke()
        :decorator:

    .. automethod:: Bot.before_invoke()
        :decorator:

    .. automethod:: Bot.check()
        :decorator:

    .. automethod:: Bot.check_once()
        :decorator:

    .. automethod:: Bot.command(*args, **kwargs)
        :decorator:
    
    .. automethod:: Bot.event()
        :decorator:

    .. automethod:: Bot.group(*args, **kwargs)
        :decorator:

    .. automethod:: Bot.listen(name=None)
        :decorator:

AutoShardedBot
~~~~~~~~~~~~~~~~

.. attributetable:: discpy.ext.commands.AutoShardedBot

.. autoclass:: discpy.ext.commands.AutoShardedBot
    :members:

Prefix Helpers
----------------

.. autofunction:: discpy.ext.commands.when_mentioned

.. autofunction:: discpy.ext.commands.when_mentioned_or

.. _ext_commands_api_events:

Event Reference
-----------------

These events function similar to :ref:`the regular events <discpy-api-events>`, except they
are custom to the command extension module.

.. function:: discpy.ext.commands.on_command_error(ctx, error)

    An error handler that is called when an error is raised
    inside a command either through user input error, check
    failure, or an error in your own code.

    A default one is provided (:meth:`.Bot.on_command_error`).

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`
    :param error: The error that was raised.
    :type error: :class:`.CommandError` derived

.. function:: discpy.ext.commands.on_command(ctx)

    An event that is called when a command is found and is about to be invoked.

    This event is called regardless of whether the command itself succeeds via
    error or completes.

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`

.. function:: discpy.ext.commands.on_command_completion(ctx)

    An event that is called when a command has completed its invocation.

    This event is called only if the command succeeded, i.e. all checks have
    passed and the user input it correctly.

    :param ctx: The invocation context.
    :type ctx: :class:`.Context`

.. _ext_commands_api_command:

Commands
----------

Decorators
~~~~~~~~~~~~

.. autofunction:: discpy.ext.commands.command
    :decorator:

.. autofunction:: discpy.ext.commands.group
    :decorator:

Command
~~~~~~~~~

.. attributetable:: discpy.ext.commands.Command

.. autoclass:: discpy.ext.commands.Command
    :members:
    :special-members: __call__
    :exclude-members: after_invoke, before_invoke, error

    .. automethod:: Command.after_invoke()
        :decorator:

    .. automethod:: Command.before_invoke()
        :decorator:

    .. automethod:: Command.error()
        :decorator:

Group
~~~~~~

.. attributetable:: discpy.ext.commands.Group

.. autoclass:: discpy.ext.commands.Group
    :members:
    :inherited-members:
    :exclude-members: after_invoke, before_invoke, command, error, group

    .. automethod:: Group.after_invoke()
        :decorator:

    .. automethod:: Group.before_invoke()
        :decorator:

    .. automethod:: Group.command(*args, **kwargs)
        :decorator:

    .. automethod:: Group.error()
        :decorator:

    .. automethod:: Group.group(*args, **kwargs)
        :decorator:

GroupMixin
~~~~~~~~~~~

.. attributetable:: discpy.ext.commands.GroupMixin

.. autoclass:: discpy.ext.commands.GroupMixin
    :members:
    :exclude-members: command, group

    .. automethod:: GroupMixin.command(*args, **kwargs)
        :decorator:

    .. automethod:: GroupMixin.group(*args, **kwargs)
        :decorator:

.. _ext_commands_api_cogs:

Cogs
------

Cog
~~~~

.. attributetable:: discpy.ext.commands.Cog

.. autoclass:: discpy.ext.commands.Cog
    :members:

CogMeta
~~~~~~~~

.. attributetable:: discpy.ext.commands.CogMeta

.. autoclass:: discpy.ext.commands.CogMeta
    :members:

.. _ext_commands_help_command:

Help Commands
---------------

HelpCommand
~~~~~~~~~~~~

.. attributetable:: discpy.ext.commands.HelpCommand

.. autoclass:: discpy.ext.commands.HelpCommand
    :members:

DefaultHelpCommand
~~~~~~~~~~~~~~~~~~~

.. attributetable:: discpy.ext.commands.DefaultHelpCommand

.. autoclass:: discpy.ext.commands.DefaultHelpCommand
    :members:
    :exclude-members: send_bot_help, send_cog_help, send_group_help, send_command_help, prepare_help_command

MinimalHelpCommand
~~~~~~~~~~~~~~~~~~~

.. attributetable:: discpy.ext.commands.MinimalHelpCommand

.. autoclass:: discpy.ext.commands.MinimalHelpCommand
    :members:
    :exclude-members: send_bot_help, send_cog_help, send_group_help, send_command_help, prepare_help_command

Paginator
~~~~~~~~~~

.. attributetable:: discpy.ext.commands.Paginator

.. autoclass:: discpy.ext.commands.Paginator
    :members:

Enums
------

.. class:: BucketType
    :module: discpy.ext.commands

    Specifies a type of bucket for, e.g. a cooldown.

    .. attribute:: default

        The default bucket operates on a global basis.
    .. attribute:: user

        The user bucket operates on a per-user basis.
    .. attribute:: guild

        The guild bucket operates on a per-guild basis.
    .. attribute:: channel

        The channel bucket operates on a per-channel basis.
    .. attribute:: member

        The member bucket operates on a per-member basis.
    .. attribute:: category

        The category bucket operates on a per-category basis.
    .. attribute:: role

        The role bucket operates on a per-role basis.

        .. versionadded:: 1.3


.. _ext_commands_api_checks:

Checks
-------

.. autofunction:: discpy.ext.commands.check(predicate)
    :decorator:

.. autofunction:: discpy.ext.commands.check_any(*checks)
    :decorator:

.. autofunction:: discpy.ext.commands.has_role(item)
    :decorator:

.. autofunction:: discpy.ext.commands.has_permissions(**perms)
    :decorator:

.. autofunction:: discpy.ext.commands.has_guild_permissions(**perms)
    :decorator:

.. autofunction:: discpy.ext.commands.has_any_role(*items)
    :decorator:

.. autofunction:: discpy.ext.commands.bot_has_role(item)
    :decorator:

.. autofunction:: discpy.ext.commands.bot_has_permissions(**perms)
    :decorator:

.. autofunction:: discpy.ext.commands.bot_has_guild_permissions(**perms)
    :decorator:

.. autofunction:: discpy.ext.commands.bot_has_any_role(*items)
    :decorator:

.. autofunction:: discpy.ext.commands.cooldown(rate, per, type=discpy.ext.commands.BucketType.default)
    :decorator:

.. autofunction:: discpy.ext.commands.dynamic_cooldown(cooldown, type=BucketType.default)
    :decorator:

.. autofunction:: discpy.ext.commands.max_concurrency(number, per=discpy.ext.commands.BucketType.default, *, wait=False)
    :decorator:

.. autofunction:: discpy.ext.commands.before_invoke(coro)
    :decorator:

.. autofunction:: discpy.ext.commands.after_invoke(coro)
    :decorator:

.. autofunction:: discpy.ext.commands.guild_only(,)
    :decorator:

.. autofunction:: discpy.ext.commands.dm_only(,)
    :decorator:

.. autofunction:: discpy.ext.commands.is_owner(,)
    :decorator:

.. autofunction:: discpy.ext.commands.is_nsfw(,)
    :decorator:

.. _ext_commands_api_context:

Cooldown
---------

.. attributetable:: discpy.ext.commands.Cooldown

.. autoclass:: discpy.ext.commands.Cooldown
    :members:

Context
--------

.. attributetable:: discpy.ext.commands.Context

.. autoclass:: discpy.ext.commands.Context
    :members:
    :inherited-members:
    :exclude-members: history, typing

    .. automethod:: discpy.ext.commands.Context.history
        :async-for:

    .. automethod:: discpy.ext.commands.Context.typing
        :async-with:

.. _ext_commands_api_converters:

Converters
------------

.. autoclass:: discpy.ext.commands.Converter
    :members:

.. autoclass:: discpy.ext.commands.ObjectConverter
    :members:

.. autoclass:: discpy.ext.commands.MemberConverter
    :members:

.. autoclass:: discpy.ext.commands.UserConverter
    :members:

.. autoclass:: discpy.ext.commands.MessageConverter
    :members:

.. autoclass:: discpy.ext.commands.PartialMessageConverter
    :members:

.. autoclass:: discpy.ext.commands.GuildChannelConverter
    :members:

.. autoclass:: discpy.ext.commands.TextChannelConverter
    :members:

.. autoclass:: discpy.ext.commands.VoiceChannelConverter
    :members:

.. autoclass:: discpy.ext.commands.StoreChannelConverter
    :members:

.. autoclass:: discpy.ext.commands.StageChannelConverter
    :members:

.. autoclass:: discpy.ext.commands.CategoryChannelConverter
    :members:

.. autoclass:: discpy.ext.commands.InviteConverter
    :members:

.. autoclass:: discpy.ext.commands.GuildConverter
    :members:

.. autoclass:: discpy.ext.commands.RoleConverter
    :members:

.. autoclass:: discpy.ext.commands.GameConverter
    :members:

.. autoclass:: discpy.ext.commands.ColourConverter
    :members:

.. autoclass:: discpy.ext.commands.EmojiConverter
    :members:

.. autoclass:: discpy.ext.commands.PartialEmojiConverter
    :members:

.. autoclass:: discpy.ext.commands.ThreadConverter
    :members:

.. autoclass:: discpy.ext.commands.GuildStickerConverter
    :members:

.. autoclass:: discpy.ext.commands.clean_content
    :members:

.. autoclass:: discpy.ext.commands.Greedy()

.. autofunction:: discpy.ext.commands.run_converters

Flag Converter
~~~~~~~~~~~~~~~

.. autoclass:: discpy.ext.commands.FlagConverter
    :members:

.. autoclass:: discpy.ext.commands.Flag()
    :members:

.. autofunction:: discpy.ext.commands.flag

.. _ext_commands_api_errors:

Exceptions
-----------

.. autoexception:: discpy.ext.commands.CommandError
    :members:

.. autoexception:: discpy.ext.commands.ConversionError
    :members:

.. autoexception:: discpy.ext.commands.MissingRequiredArgument
    :members:

.. autoexception:: discpy.ext.commands.ArgumentParsingError
    :members:

.. autoexception:: discpy.ext.commands.UnexpectedQuoteError
    :members:

.. autoexception:: discpy.ext.commands.InvalidEndOfQuotedStringError
    :members:

.. autoexception:: discpy.ext.commands.ExpectedClosingQuoteError
    :members:

.. autoexception:: discpy.ext.commands.BadArgument
    :members:

.. autoexception:: discpy.ext.commands.BadUnionArgument
    :members:

.. autoexception:: discpy.ext.commands.BadLiteralArgument
    :members:

.. autoexception:: discpy.ext.commands.PrivateMessageOnly
    :members:

.. autoexception:: discpy.ext.commands.NoPrivateMessage
    :members:

.. autoexception:: discpy.ext.commands.CheckFailure
    :members:

.. autoexception:: discpy.ext.commands.CheckAnyFailure
    :members:

.. autoexception:: discpy.ext.commands.CommandNotFound
    :members:

.. autoexception:: discpy.ext.commands.DisabledCommand
    :members:

.. autoexception:: discpy.ext.commands.CommandInvokeError
    :members:

.. autoexception:: discpy.ext.commands.TooManyArguments
    :members:

.. autoexception:: discpy.ext.commands.UserInputError
    :members:

.. autoexception:: discpy.ext.commands.CommandOnCooldown
    :members:

.. autoexception:: discpy.ext.commands.MaxConcurrencyReached
    :members:

.. autoexception:: discpy.ext.commands.NotOwner
    :members:

.. autoexception:: discpy.ext.commands.MessageNotFound
    :members:

.. autoexception:: discpy.ext.commands.MemberNotFound
    :members:

.. autoexception:: discpy.ext.commands.GuildNotFound
    :members:

.. autoexception:: discpy.ext.commands.UserNotFound
    :members:

.. autoexception:: discpy.ext.commands.ChannelNotFound
    :members:

.. autoexception:: discpy.ext.commands.ChannelNotReadable
    :members:

.. autoexception:: discpy.ext.commands.ThreadNotFound
    :members:

.. autoexception:: discpy.ext.commands.BadColourArgument
    :members:

.. autoexception:: discpy.ext.commands.RoleNotFound
    :members:

.. autoexception:: discpy.ext.commands.BadInviteArgument
    :members:

.. autoexception:: discpy.ext.commands.EmojiNotFound
    :members:

.. autoexception:: discpy.ext.commands.PartialEmojiConversionFailure
    :members:

.. autoexception:: discpy.ext.commands.GuildStickerNotFound
    :members:

.. autoexception:: discpy.ext.commands.BadBoolArgument
    :members:

.. autoexception:: discpy.ext.commands.MissingPermissions
    :members:

.. autoexception:: discpy.ext.commands.BotMissingPermissions
    :members:

.. autoexception:: discpy.ext.commands.MissingRole
    :members:

.. autoexception:: discpy.ext.commands.BotMissingRole
    :members:

.. autoexception:: discpy.ext.commands.MissingAnyRole
    :members:

.. autoexception:: discpy.ext.commands.BotMissingAnyRole
    :members:

.. autoexception:: discpy.ext.commands.NSFWChannelRequired
    :members:

.. autoexception:: discpy.ext.commands.FlagError
    :members:

.. autoexception:: discpy.ext.commands.BadFlagArgument
    :members:

.. autoexception:: discpy.ext.commands.MissingFlagArgument
    :members:

.. autoexception:: discpy.ext.commands.TooManyFlags
    :members:

.. autoexception:: discpy.ext.commands.MissingRequiredFlag
    :members:

.. autoexception:: discpy.ext.commands.ExtensionError
    :members:

.. autoexception:: discpy.ext.commands.ExtensionAlreadyLoaded
    :members:

.. autoexception:: discpy.ext.commands.ExtensionNotLoaded
    :members:

.. autoexception:: discpy.ext.commands.NoEntryPointError
    :members:

.. autoexception:: discpy.ext.commands.ExtensionFailed
    :members:

.. autoexception:: discpy.ext.commands.ExtensionNotFound
    :members:

.. autoexception:: discpy.ext.commands.CommandRegistrationError
    :members:


Exception Hierarchy
~~~~~~~~~~~~~~~~~~~~~

.. exception_hierarchy::

    - :exc:`~.DiscordException`
        - :exc:`~.commands.CommandError`
            - :exc:`~.commands.ConversionError`
            - :exc:`~.commands.UserInputError`
                - :exc:`~.commands.MissingRequiredArgument`
                - :exc:`~.commands.TooManyArguments`
                - :exc:`~.commands.BadArgument`
                    - :exc:`~.commands.MessageNotFound`
                    - :exc:`~.commands.MemberNotFound`
                    - :exc:`~.commands.GuildNotFound`
                    - :exc:`~.commands.UserNotFound`
                    - :exc:`~.commands.ChannelNotFound`
                    - :exc:`~.commands.ChannelNotReadable`
                    - :exc:`~.commands.BadColourArgument`
                    - :exc:`~.commands.RoleNotFound`
                    - :exc:`~.commands.BadInviteArgument`
                    - :exc:`~.commands.EmojiNotFound`
                    - :exc:`~.commands.GuildStickerNotFound`
                    - :exc:`~.commands.PartialEmojiConversionFailure`
                    - :exc:`~.commands.BadBoolArgument`
                    - :exc:`~.commands.ThreadNotFound`
                    - :exc:`~.commands.FlagError`
                        - :exc:`~.commands.BadFlagArgument`
                        - :exc:`~.commands.MissingFlagArgument`
                        - :exc:`~.commands.TooManyFlags`
                        - :exc:`~.commands.MissingRequiredFlag`
                - :exc:`~.commands.BadUnionArgument`
                - :exc:`~.commands.BadLiteralArgument`
                - :exc:`~.commands.ArgumentParsingError`
                    - :exc:`~.commands.UnexpectedQuoteError`
                    - :exc:`~.commands.InvalidEndOfQuotedStringError`
                    - :exc:`~.commands.ExpectedClosingQuoteError`
            - :exc:`~.commands.CommandNotFound`
            - :exc:`~.commands.CheckFailure`
                - :exc:`~.commands.CheckAnyFailure`
                - :exc:`~.commands.PrivateMessageOnly`
                - :exc:`~.commands.NoPrivateMessage`
                - :exc:`~.commands.NotOwner`
                - :exc:`~.commands.MissingPermissions`
                - :exc:`~.commands.BotMissingPermissions`
                - :exc:`~.commands.MissingRole`
                - :exc:`~.commands.BotMissingRole`
                - :exc:`~.commands.MissingAnyRole`
                - :exc:`~.commands.BotMissingAnyRole`
                - :exc:`~.commands.NSFWChannelRequired`
            - :exc:`~.commands.DisabledCommand`
            - :exc:`~.commands.CommandInvokeError`
            - :exc:`~.commands.CommandOnCooldown`
            - :exc:`~.commands.MaxConcurrencyReached`
        - :exc:`~.commands.ExtensionError`
            - :exc:`~.commands.ExtensionAlreadyLoaded`
            - :exc:`~.commands.ExtensionNotLoaded`
            - :exc:`~.commands.NoEntryPointError`
            - :exc:`~.commands.ExtensionFailed`
            - :exc:`~.commands.ExtensionNotFound`
    - :exc:`~.ClientException`
        - :exc:`~.commands.CommandRegistrationError`
