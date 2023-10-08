# First Steps

Now that you have Venera installed following [[Installation]], after before steps it must be ready to go. To run it, open a new command line and run the binary with the `venera` command, this should load a new interactive prompt, the tool's interface where the user should take their actions.

After `venera` starts up, it must present a banner containing version information and the repository in addition to its name.

You will notice that there are no scripts to be executed, that is, the tool does nothing. The first thing you must is to download the scripts from the official repository, or whatever else you want. Do this by using [[Venera Package Manager]] (VPM), a built-in package manager for scripts.

## Syncing With The Main Repository

The main repository from where the scripts will be downloaded is `http://r.venera.farinap5.com/package.yaml`, you can see it and change for another by using [[Global Variables]].

Type the `sync` command from VPN and synchronize the scripts.

```
[vnr]>> vpm sync
[vnr]>> vpm sync
[OK]- Requesting http://r.venera.farinap5.com/package.yaml                              

[!]- Intalling /web/trace.lua
[OK]- /web/trace.lua installed.
[!]- Intalling /web/ngx1.lua
[OK]- /web/ngx1.lua installed.
[!]- Intalling /web/gen_ssti_jinja.lua
[OK]- /web/gen_ssti_jinja.lua installed.
...
```

Type `reload root` to refresh the scrpts search engine.
## Using Scripts

There are already some scripts to be used. Several scripts were installed for testing, example scripts, and general use scripts.

Type the command `use` followed by any script, the suggestions may give some examples.

```
[vnr]>> use /root/.venera/scripts/test/http.lua
```

After loading the script, type `info` to show some data regarding it.

```
(/root/.venera/scripts/test/http.lua)>> info
## AUTHOR/S ##
1) Author1 <author1@mail.com>

## TAGS ##
1) example
2) http

## INFO ##
HTTP requests with lua-go
(/root/.venera/scripts/test/http.lua)>>
```

Type `options` to see the parameters.

```
(/root/.venera/scripts/test/http.lua)>> options

VARIABLE  DEFAULT             REQUIRED  DESCRIPTION
--------  -------             --------  -----------
URL       http://example.com  yes       URL
METHOD    GET                 yes       METHOD
```

Let's reset the `URL`.

```
(/root/.venera/scripts/test/http.lua)>> set URL http://example.com/
[OK] URL <- http://example.com/
(/root/.venera/scripts/test/http.lua)>> options

VARIABLE  DEFAULT              REQUIRED  DESCRIPTION
--------  -------              --------  -----------
URL       http://example.com/  yes       URL
METHOD    GET                  yes       METHOD

(/root/.venera/scripts/test/http.lua)>>
```

Now you may execute it by typing `run`.

```
(/root/.venera/scripts/test/http.lua)>> run
[OK]- 200
[OK]- <!doctype html>
<html>
	<head>
		<title>Example Domain</title>
		<meta charset="utf-8" />
		<meta http-equiv="Content-type" content="text/html; charset=utf-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1" />
		<style type="text/css">
		...
```

Awesome. Venera is working as expected!