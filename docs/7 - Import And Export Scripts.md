If you have a script outside the tool and want to import it so that it can be found by the Venera, there are a few ways. In fact, there are a few ways to show the venerate where the script is.

The first way is to place the script manually in the scripts folder, usually `~/.venera/scripts/*`. Then, you choose the subfolder that makes sense. But there are other methods.
## Impot Script
The first method is to script it with the `import` command.

```
[vnr]>> import /home/user/Desktop/myscript.lua /myscript.lua
```

Where was the script actually positioned on my system? This can be seen by the global variable `myscripts`.

```
[vnr]>> globals

VARIABLE    VALUE
--------    -----
...
myscripts   /home/pietro/.venera/scripts/myscripts/
...
```

Now, reload the root.

```
[vnr]>> reload root
```

And Venera know about your script. You can search for it.

## Export Script
The way to export a script is similar, use the `export` command.

```
[vnr]>> myscript.lua /home/user/Desktop/myscript.lua
```