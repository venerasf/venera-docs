# Table METADATA

`METADATA` takes information reguarding the script so Venera can identify this module in its script base, all fields need to be configured properly.

- `AUTHOR` is a list of strings, others who created the script or have participated in research for that flaw it abuses as example.
- `VERSION` module/script version.
- `TAGS` Some tags that define the script and its purpose. Scripts can be searched and executed based on their tags.
- `INFO` The description of the script may have, flaw that it abuses, type of test, proposed mitigations, it's up to the creator.

```lua
METADATA = {
    AUTHOR = {"Author1 <author1@mail.com>","Author2 <author2@mail.com>"},
    VERSION = "0.1",
    TAGS = {"example","http","scanner"},
    INFO = [[HTTP requests with lua-go]]
}
```

This data is used by Venera Search Engine to index the script, list and so on.