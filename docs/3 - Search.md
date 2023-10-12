# Search Command

The `search` command allows searching and listing scripts by assigning different filtering parameters.

The use is very straight forward as it takes proprieties from name, path and metadata to bring results. 

Just by typing `search` it will show all listable scripts containing in the database.

```
[*]>> search

COUNT  PATH                                     DESCRIPTION                   TAGS
-----  ----                                     -----------                   ----
1      scripts/cms/wp_user_enum.lua             Wordpress user enumeratio...  enum,http,wordpress,scann
2      scripts/cve/cve-2014/CVE-2014-6271.lua   Shellshock Remote Code Ex...  cve,rce,http,bash,scanner
3      scripts/cve/cve-2021/CVE-2021-40978.lua  LFI affecting MKDocs 1.2....  cve,lfi,http,mkdocs,scann
4      scripts/myscripts/meynewsc.lua           IE test                       example,XSS,scanner
5      scripts/test/base64.lua                  Lorem ipsum dolor sit ame...  example,encoding,util
...
```

It is possible to apply filters like `match` keyword that will filter using a matching pattern.

```
[*]>> search match <substring>
```

It is possible to specify whether the searched pattern can be found in places such as the path or description of the script.

```
search match:path <substring>
search match:description <substring>
```

The main way to search for specific scripts is by tag search. It can be done with the `tag` parameter.

```
search tag <tag1 tag2...>
```

The following example illustrates the usability.

```
[*]>> serach tag nginx apache 
```