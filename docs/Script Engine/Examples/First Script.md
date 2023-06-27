Putting together everything seen before, write a script capable of printing what is defined by the user through the command line, so when the user initializes the `main()` function of the script through the command line using the `run` command, this string should appear on the screen.

Create a script `/tmp/test.lua` and write the following content:

```lua
METADATA = {
    AUTHOR = {"Author1 <author1@mail.com>",
                "Author2 <author2@mail.com>",
                "Author3 <author3@mail.com>"
            },
    VERSION = "0.1",
    TAGS = {"example","test"},
    INFO = [[Lorem ipsum dolor sit amet, consectetur adipiscing elit,
sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
nisi ut aliquip ex ea commodo consequat.]]
}

VARS = {
    DATA = {VALUE="my data", NEEDED="yes", DESCRIPT="Any"},
}

function Init()
    Meta(METADATA)
    LoadVars(VARS)
end

function Main()
    PrintSuccs(VARS.DATA.VALUE)
end
```

It is necessary to import the script into a directory where `venera` has access. Use the `import` command as shown below:

```
[*]>> import /tmp/test.lua test.lua
```

The script was written in location `scripts/myscripts/test.lua`. Load the imported script with `use` command:

```
[*]>> use scripts/myscripts/test.lua
(scripts/myscripts/test.lua)>> 
```

The moment the script has been loaded, the `Init()` function is executed, loading the essential tables (METADATA and VARS) and any code that exists there.

Type `info` to show information about the script:

```
(scripts/myscripts/test.lua)>> info
## AUTHOR/S ##
1) Author1 <author1@mail.com>
2) Author2 <author2@mail.com>
3) Author3 <author3@mail.com>

## TAGS ##
1) example
2) test

## INFO ##
Lorem ipsum dolor sit amet, consectetur adipiscing elit,
sed do eiusmod tempor incididunt ut labore et dolore magna aliqua.
Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris
nisi ut aliquip ex ea commodo consequat.
```

Type `options` to see what the user can configure: 

```
(scripts/myscripts/test.lua)>> options

VARIABLE  DEFAULT  REQUIRED  DESCRIPTION
--------  -------  --------  -----------
DATA      my data  yes       Any
```

Set any value to the `DATA` variable with the command `set`:

```
(scripts/myscripts/test.lua)>> set DATA Hello World\n
[OK] DATA <- Hello World\n
```

And finally execute the script:

```
(scripts/myscripts/test.lua)>> run
[OK]- Hello World
```