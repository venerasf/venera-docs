# Built-in Functions

Venera has built-in functions allowing you to call them from within your script. This makes it possible to define standards, giving the script developer the sole concern of writing the script, without thinking too much about how it will behave in terms of interaction with the environment.

## Printing

`PrintSuccs( str )` Print success message.

`PrintErr( str )` Print error message.

`PrintInfo( str )` Print info message.

`PrintSuccsln( str )` Print success message with line ending.

`PrintErrln( str )` Print error message with line ending.

`PrintInfoln( str )` Print info message with line ending.

`Print( str )` Print string.

`Println( str )` Print string with line ending.

## Interaction

`Input( str ) -> str` Prompt for an user input.

## Interact with  Scripts and Files

`Call( path=str )` Call another script/module. The `VARS` ([[Variables]]) from caller scripts are inherited by scripts being called.

`Open( str ) -> str` Read a local file.