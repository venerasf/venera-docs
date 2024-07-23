# Table VARS

`VARS` table loads the script's variables, which it uses as parameters for its actions.

```lua
VARS = {
    URL = {VALUE="http://example.com", NEEDED="yes", DESCRIPT="URL"},
    METHOD = {VALUE="GET", NEEDED="yes", DESCRIPT="METHOD"}
}
```

When the variables are setted in `VARS` table, the user is able to interact with them using the command `options` to list those variables, and then the command `set` to configure a value for a variable:

```
(scripts/test/http.lua)>> options

VARIABLE  DEFAULT             NEEDED  DESCRIPTION
--------  -------             ------  -----------
URL       http://example.com  yes     URL
METHOD    GET                 yes     METHOD
```

As mentioned, user also can edit those variables with the `set` command:

```
(scripts/test/http.lua)>> set URL http://google.com
[OK] URL <- http://google.com
```

Then `URL` value has been changed.

```
(scripts/test/http.lua)>> options

VARIABLE  DEFAULT             NEEDED  DESCRIPTION
--------  -------             ------  -----------
URL       http://google.com   yes     URL
METHOD    GET                 yes     METHOD
```

When writing your scripts you may access the value by simply using the value direct from the table:

```
function Main()
    local request = http.request(VARS.METHOD.VALUE, VARS.URL.VALUE)
    local result, err = client:do_request(request)
```