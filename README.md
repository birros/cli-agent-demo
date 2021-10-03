# cli-agent-demo

This repo shows how to create and keep a token during a shell session that it is
only accessible to a given program. Useful to create a cli program asking to
enter a password and avoid to be asked every time. As it is the case for `ssh`
or `sudo`.

This trick is based on the fact that aliases are not inherited.

## Setup for the example

```shell
$ PATH="$PWD/bin:$PATH"
```

## Workflow example

```shell
$ eval $(prog --agent) # set it in shell rc (eg .bashrc) as for ssh-agent

$ prog lorem_ipsum
PROG_SHELL_TOKEN=092927209144713d9dc0e0e316cd665f1668b59f63003e99b4482f92c7bd1a83
args:lorem_ipsum

$ prog2 lorem_ipsum
PROG_SHELL_TOKEN=
PROG_SHELL_TOKEN=
args:lorem_ipsum

$ unalias prog

$ prog lorem_ipsum
PROG_SHELL_TOKEN=
args:lorem_ipsum
```
