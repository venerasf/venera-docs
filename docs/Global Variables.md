
The global variable acts like a simple key-value database. It must be used for storing data that can be accessed globally by the core tool and the scripts executed.

Global variables are persistent, and will remain set between sessions.

## How it Works

The way to configure a global variable is exactly the same as how to configure a script variable. The user uses the `set` command followed by the key and the values to assign for that specific key.

What changes is that it is now necessary to use the `global` keyword after the `set` command.

```
[*]>> set global <key> <value>
```

The way of viewing the global variables is simple, just type `globals` and the output will contain all the variables already set so far.

```
[*]>> globals

VARIABLE   VALUE
--------   -----
key        value
chain      on
VERBOSE    true
user       username
test       test
myscripts  myscripts/
logfile    ~/.venera/message.log
```

## Use Cases

Global variables, just like environment variables of an operating system, will contain some options that the core tool will take into account when taking some actions.

For instance, it is possible to configure the location where `venera` stores the execution log, it is taken from the global variable `logfile` so altering the value will change the place to keep the debugging data. You could prefer keep this type of data under /var/log or other place, globals is where to change this.

## Automate Script Configuration

Let's assume we want to perform a security test with the script `scripts/web/ngx1.lua`.

The only variable the script requires to be set is the `URL` variable. It keeps the url of the remote host.

```
(scripts/web/ngx1.lua)>> options

VARIABLE  DEFAULT             REQUIRED  DESCRIPTION
--------  -------             --------  -----------
URL       http://example.com  yes       URL
```

The `URL` variable, using globals, can be configured globally, so it is possible to persist this data for future use.

So if this variable is common, it is possible to set it outside the script and whenever you enter a script that requires the `URL` variable it will be set automatically from globals.

Configure the variable `URL`.

```
[*]>> set global URL http://mydomain.com
```

And load the script.

```
[*]>> use scripts/web/ngx1.lua
[OK] URL <- http://mydomain.com
(scripts/web/ngx1.lua)>> options

VARIABLE  DEFAULT              REQUIRED  DESCRIPTION
--------  -------              --------  -----------
URL       http://mydomain.com  yes       URL
```

Notice that the variable was set automatically.