Environment Variables

Defining a variable for the current session -- Does not cross over to new sessions:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
[variablename]=[variabledefinition]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

$variablename will call the variabledefined

Defining a global variable -- Crosses sessions but does not go beyond a reboot:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
export [variablename]=[variabledefinition]
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Displaying current environment variables -- Can be changed/modified:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
env
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
