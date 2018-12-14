# CHANGELOG

### 0.8.0 - (2018-12-14)

* __feature__  
  string interpolation  
  the values of variables are substituted into string literals  
  string interpolation works for double-quoted strings and default strings 
  example:  
  ~~~
  $object = house
  setup "This is a $(object)."
  # => { setup: "This is a house." }
  ~~~

* __feature__  
  schema definition:  
  if there are more values listed than keys for the schema specifier are defined, then an exception is raised  
  if there are less values listed than keys for the schema specifier are defined, then only the keys for the available values will be set

* __breaking change__, __bugfix__  
  in array definition with schema specifier  
  syntax change: now after colon (:) for defining a hash, there needs to be at least one space character between the colon
  and the next expression on the same line

* __feature__  
  schema specifiers can now also be defined at the time of use   
  example:  
  ~~~
  persons1 , @schema person(firstname,lastname,age)
    : Harry   | Langemann | 44
    : Susi    | Heimstett | 32
  persons2 , @schema person  
    : Ludwig  | Reinemann | 33
  ~~~

* __feature__  
  anonymous schema specifiers  
  defined when used, defined without a name, for one-time use  
  example:  
  ~~~
  persons , @schema(firstname,lastname,age)  
    : Harry | Langemann | 44
  ~~~

* __breaking change__  
  change of the definition of a schema specifier  
    before : $name(key1,key2,...)  
    now    : @schema name(key1,key2,...)  
    this makes it different from variables  
  change of the use of a schema specifier  
    before : , $name  
    now    : , @schema name
  
* __breaking change__  
  default strings are no longer allowed to begin with one of the following characters: ;$!@&*:,  
  exception is a beginning string interpolation: $(var)
  
* __feature__  
  for a reference (e.g. ref)
  @merge *ref    : in a hash  
  @insert *ref   : in an array

* __feature__  
  supporting references, definition: &ref, use: *ref  
  if a reference is used which was not defined before, then an exception is raised

* __feature__  
  @na directive (na = not available) inside definitions with schema specifiers

* __feature__  
  if a schema specifier is used which was not defined before, then an exception is raised

* __feature__  
  supporting variables, $variable  
  if a variable is used which was not defined before, then an exception is raised

### 0.7.1 - (2018-11-12)

* __bugfix__  
  again an error in escaping single-quoted and double-quoted strings  
  
