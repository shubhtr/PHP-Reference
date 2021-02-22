# PHP Reference
## by Shubhrendu Tripathi

<br><br>

## Variables and Constants

### Defining Variables

### Types of Data

### Variable Scope

### Predefined Variables

### Variable-handling Functions

## If-Else

# Loops

In PHP, we have the following loop types:

while - loops through a block of code as long as the specified condition is true
do...while - loops through a block of code once, and then repeats the loop as long as the specified condition is true
for - loops through a block of code a specified number of times
foreach - loops through a block of code for each element in an array

## while

Loops through a block of code as long as the specified condition is true

Example - display numbers from 1 to 5:

    <?php
    $x = 1;

    while($x <= 5) {
    echo "The number is: $x <br>";
    $x++;
    }
    ?>

Example - counts to 100 by tens:

    <?php
    $x = 0;

    while($x <= 100) {
    echo "The number is: $x <br>";
    $x+=10;
    }
    ?>



## do while

Loops through a block of code once, and then repeats the loop as long as the specified condition is true.

Example:

    <?php
    $x = 1;

    do {
    echo "The number is: $x <br>";
    $x++;
    } while ($x <= 5);
    ?>

Example 2:

    <?php
    $x = 6;

    do {
    echo "The number is: $x <br>";
    $x++;
    } while ($x <= 5);
    ?>

## for

Loops through a block of code a specified number of times.

Example: 

    <?php
    for ($x = 0; $x <= 10; $x++) {
    echo "The number is: $x <br>";
    }
    ?>

Example - count by tens:

    <?php
    for ($x = 0; $x <= 100; $x+=10) {
    echo "The number is: $x <br>";
    }
    ?>

## foreach

    foreach ($array as $value) {
        code to be executed;
    }

Example - values:

    <?php
    $colors = array("red", "green", "blue", "yellow");

    foreach ($colors as $value) {
    echo "$value <br>";
    }
    ?>

Example - key,value:

    <?php
    $age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");

    foreach($age as $x => $val) {
        echo "$x = $val<br>";
    }
    ?>

## break/continue

### break

<ul>
<li>used to "jump out" of a switch statement.</li>
<li>used to jump out of a loop</li>
</ul>

    <?php
    for ($x = 0; $x < 10; $x++) {
    if ($x == 4) {
        break;
    }
    echo "The number is: $x <br>";
    }
    ?>

### continue

<ul>
<li>breaks one iteration (in the loop), if a specified condition occurs, and continues with the next iteration in the loop.</li>
</ul>

    <?php
    for ($x = 0; $x < 10; $x++) {
    if ($x == 4) {
        continue;
    }
    echo "The number is: $x <br>";
    }
    ?>

## Switch

### Ternary Operator

    (Condition) ? (Statement1) : (Statement2);

<ul>
<li><b>Condition</b>: It is the expression to be evaluated which returns a boolean value.</li>
<li><b>Statement 1</b>: it is the statement to be executed if the condition results in a true state.</li>
<li><b>Statement 2</b>: It is the statement to be executed if the condition results in a false state.</li>
</ul>

Example

    <?php
    $marks=40;
    print ($marks>=40) ? "pass" : "Fail";
    ?>

Output

    pass

### Modules

    $ php -m

### Constants

Constants are like variables except that once they are defined they cannot be changed or undefined.

    define(name, value, true/false)

    name: Specifies the name of the constant
    value: Specifies the value of the constant
    case-insensitive: Specifies whether the constant name should be case-insensitive. Default is false

A class constant is declared inside a class with the const keyword.

    <?php
    class Goodbye {
    const LEAVING_MESSAGE = "Thank you for visiting W3Schools.com!";
    }

    echo Goodbye::LEAVING_MESSAGE;
    ?>

Constant Arrays

Create an Array constant using the define() function.

    <?php
    define("cars", [
    "Alfa Romeo",
    "BMW",
    "Toyota"
    ]);
    echo cars[0];
    ?>

### exit()

    <?php
    $site = "https://www.w3schools.com/";
    fopen($site,"r") or exit("Unable to connect to $site");
    ?>

### die()

alias for exit() function

    <?php
    $site = "https://www.w3schools.com/";
    fopen($site,"r") or die("Unable to connect to $site");
    ?>

#### Default PHP constants

Constant                | Description
---                     | ---
`__LINE__`              | denotes the number of the current line in a file
`__FILE__`              | is the full path and filename of the file
`__DIR__`               | directory of the file
`__FUNCTION__`          | name of the function
`__CLASS__`             | class name, includes the namespace it was declared in
`__TRAIT__`             | the trait name, also includes the namespace
`__METHOD__`            | the class method name
`__NAMESPACE__`         | name of the current namespace

## array

## return

## namespace

I.
With the setup you have here. You would have to execute the following to fire that function.

(new MyFunctions\basic)->say_hello("Bob");
(I dont recommend this method, it creates an object for no reason.)

What I'm assuming you wanted was:

namespace MyFunctions;

function say_hello($a)
{
    echo "Hello, $a";
}
at which point you could use

// this gives you 'Hello, Bob'
MyFunctions\say_hello("Bob");

II.
ClassNames are considered relative to the current namespace unless they start with a \

This means that inside the MicrosoftAzure\Storage namespace you can use the relative namespace for class.

If you want to call a class from a different namespace you should call fully-qualified name for it like

    $action = \MicrosoftAzure\WhereEver\MicroGrid::GetParameter('action');
or use the name space or unique class with fully-qualified name

    use \MicrosoftAzure\WhereEver;
or

    use \MicrosoftAzure\WhereEver\MicroGrid;
then:

    $action = MicroGrid::GetParameter('action');
Edited to make it clear

namespaces allow us to avoid naming collisions and to alias long names caused by avoiding naming collisions.

it depends to your autoloader for a simple example I create a new project and make this autoloader in the index.php located at root directory

function __autoload($className){
    //if it's a full name with windows style slashes correct the path
    $file_name = str_replace('\\', '/', $className);
    require_once("vender/src/".$file_name.".php");
}
when I call $date = new \App\Utility\Date(); autoloader will require this file:

verdor/src/App/Utility/Date.php
and in Date.php I used this name space namespace App\Utility;



## require_once

## dirname(__FILE__)

## use

## function

## throw - try - catch - Exception

# Error reporting 

    ini_set('display_errors', 1);
    error_reporting(E_ALL);

# PHP OOP

OOP - Object Oriented Programming
<ul>
<li>faster and easier to execute</li>
<li>provides a clear structure for the programs</li>
<li>helps keep the PHP code DRY, and makes the code easier to maintain, modify and debug</li>
<li>makes its possible to create fully resuable applications with less code and shorter development time</li>
</ul>

DRY - "Don't Repeat Yourself" - reducing the repetition of code. Extract the logic that is common to the application, and place it in a single place and resuse them instead of repeating it.

## Class and Object

Class is a template for objects.

Object is an instance of a class. When the individual objects are created, they inherit all the properties and behaviors from the class, but each object will have different values for the properties.


### class

    <?php
    class Fruit {
        //properties
        public $name;
        public $color;

        //methods
        function set_name($name) {
            $this->name = $name;
        }
        function get_name() {
            return $this->name;
        }
    }
    ?>

<ins>Note</ins>: In a class, variables are called properties and functions are called methods.

### object

Objects of a class are created using the `new` keyword. Each object has all the properties and methods defined in the class, but they will have different property values.

    <?php
    class Fruit {
        //properties
        public $name;
        public $color;

        //methods
        function set_name($name){
            $this->name = $name;
        }
        function get_name(){
            return $this->name;
        }
        function set_color($color) {
            $this->color = $color;
        }
        function get_color(){
            return $this->color;
        }
    }

    $apple = new Fruit();
    $banana = new Fruit();

    $apple->set_name('apple');
    $apple->set_color('red');

    $banana->set_name('banana');

    echo $apple->get_name();
    echo "<br>";
    echo $apple->get_color();
    echo "<br>";
    echo $banana->get_name();
    ?>

### $this

`$this` keyword refers to the current object, and is only available inside methods.

    <?php
    class Fruit {
    public $name;
    }
    $apple = new Fruit();
    ?>

### change a property

(1) inside the class - by adding a set_name() method and use $this

    <?php
    class Fruit {
        public $name;
        function set_name($name) {
            $this->name = $name;
        }
    }
    $apple = new Fruit();
    $apple->set_name("Apple");
    ?>

(2) outside the class - by directly changing the property value

    <?php
    class Fruit {
        public $name;
    }
    $apple = new Fruit();
    $apple->name = "Apple";
    ?>

### instanceof 

use the `instanceof` keyword to check if an object belongs to a specific class

    <?php
    $apple = new Fruit();
    var_dump($apple instanceof Fruit);
    ?>

### Constructor

`__construct()` - PHP will automatically call this function when you create an object from a class.

    ```php
    <?php
    class Fruit {
        public $name;
        public $color;

        function __construct($name) {
            $this->name = $name;
        }
        function get_name() {
            return $this->name;
        }
    }

    $apple = new Fruit("Apple");
    echo $apple->get_name();
    ?>
    ```

### call parent constructor in child class

a call to parent::__construct() within the child constructor is required

    <?php
    class grandpa{
        public function __construct(){
            echo "I am in Tutorials Point"."\n";
        }
    }
    class papa extends grandpa{
        public function __construct(){
            parent::__construct();
            echo "I am not in Tutorials Point";
        }
    }
    $obj = new papa();
    ?>

    
### private

### public


## File Operations

### fopen
<ins>Description:</ins> open a file

    <?php
        $myfile = fopen("dictionary.txt", "r") or die("Unable to open file!");
        echo fread($myfile, filesize("dictionary.txt"));
        fclose($myfile);
    ?>

Modes | Description
--- | ---
r | <b>Open a file for read only.</b> File pointer starts at the beginning of the file
w | <b>Open a file for write only.</b> Erases the contents of the file or creates a new file if it doesn't exist. File pointer starts at the beginning of the file
a | <b>Open file for write only.</b> The existing data in file is preserved. File pointer starts at the end of the file. Creates a new file if the file doesn't exist.
x | <b>Creates a new file for write only.</b> Returns FALSE and an error if file already exists
r+ | <b>Open a file for read/write.</b> File pointer starts at the beginning of the file .
w+ | <b>Open a file for read/write.</b> Erases the contents of the file or creates a new file it it doesn't exist. File pointer starts at the beginning of the file. 
a+ | <b>Open a file for read/write.</b> The existing data in file is preserved. File pointer starts at the end of the file. Creates a new file if the file doesn't exist.
x+ | <b>Creates a new file for read/write.</b> Returns FALSE and an error if file already exists. 

### fread
<ins>Description:</ins> read from a file

    fread($myfile, filesize("dictionary.txt"));

### fclose
<ins>Description:</ins> close an open file

    <?php
        $myfile = fopen("dictionary.txt", "r");
        //some code to be executed...
        fclose($myfile);
    ?>

## Keywords

PHP has a set of keywords that are reserved words which cannot be used as function names, class names or method names. Prior to PHP 7, these keywords could not be used as class property names either:

Keyword             |   Description
---                 |   ---
abstract            |	Declare a class as abstract
and	                |   A logical operator
as	                |   Used in the foreach loop
break               |	Break out of loops and switch statements
callable	        |   A data type which can be executed as a function
case	            |   Used in the switch conditional
catch	            |   Used in the try..catch statement
class	            |   Declare a class
clone	            |   Create a copy of an object
const	            |   Define a class constant
continue            |   Jump to the next iteration of a loop
declare	            |   Set directives for a block of code
default	            |   Used in the switch statement
do	                |   Create a do...while loop
echo                |	Output text
else                |	Used in conditional statements
elseif              |	Used in conditional statements
empty	            |   Check if an expression is empty
enddeclare          |	End a declare block
endfor	            |   End a for block
endforeach	        |   End a foreach block
endif	            |   End an if or elseif block
endswitch           |	End a switch block
endwhile            |	End a while block
extends	            |   Extends a class or interface
final	            |   Declare a class, property or method as final
finally	            |   Used in the try...catch statement
fn	                |   Declare an arrow function
for	                |   Create a for loop
foreach	            |   Create a foreach loop
function            |	Create a function
global	            |   Import variables from the global scope
goto	            |   Jump to a line of code
if	                |   Create a conditional statement
implements          |   Implement an interface
include	            |   Embed code from another file
include_once        |	Embed code from another file
instanceof	        |   Test an object's class
insteadof	        |   Resolve conflicts with traits
interface	        |   Declare an interface
isset	            |   Check if a variable exists and is not null
list	            |   Assigns array elements into variables
namespace	        |   Declares a namespace
new	                |   Creates an object
or	                |   A logical operator
print               |	Output text
private	            |   Declare a property, method or constant as private
protected	        |   Declare a property, method or constant as protected
public	            |   Declare a property, method or constant as public
require	            |   Embed code from another file
require_once	    |   Embed code from another file
return	            |   Exit a function and return a value
static	            |   Declare a property or method as static
switch	            |   Create a switch block
throw	            |   Throw an exception
trait	            |   Declare a trait
try	                |   Create a try...catch structure
unset               |	Delete a variable or array element
use	                |   Use a namespace <br> <ol><li>It tells a class to inherit a trait and,</li><li>it gives an alias to a namespace.</li></ol>
var	                |   Declare a variable
while               |	Create a while loop or end a do...while loop
xor	                |   A logical operator
yield               |	Used in generator functions
yield from	        |   Used in generator functions

## Format a number with leading zeros 

sprintf()
substr()

<ins>Example 1</ins>

    <?php 
        $var = 1234567; 
        echo sprintf('%08d', $var); 
    ?> 

<ins>Example 2</ins> - negative numbers with leading zeroes

    <?php 
        $var1 = -10; 
        $var2 = 10; 
        echo sprintf('%04d', $var1) . "\n"; 
        echo sprintf('%04d', $var2); 
    ?> 

<ins>Example 3</ins> - using substr() function

    <?php 
        $num = 123; 
        $str_length = 4; 
        
        // Left padding if number < $str_length 
        $str = substr("0000{$num}", -$str_length); 
        echo sprintf($str); 
    ?> 

str_pad 

    str_pad($value, 8, '0', STR_PAD_LEFT);

<ins>Note:</ins> Not an option with negative numbers.

## destroy an object

You're looking for unset().

But take into account that you can't explicitly destroy an object.

It will stay there, however if you unset the object and your script pushes PHP to the memory limits the objects not needed will be garbage collected. I would go with unset() (as opposed to setting it to null) as it seems to have better performance (not tested but documented on one of the comments from the PHP official manual).

That said, do keep in mind that PHP always destroys the objects as soon as the page is served. So this should only be needed on really long loops and/or heavy intensive pages.


# php Command Line options

Example: 

    $ php -m

Option | Description 
--- | ---
-a                      |   Run interactively
-c <`path`>\|<`file`>   |   Look for php.ini file in this directory
-n                      |   No php.ini file will be used
-d foo[`=bar`]          |   Define INI entry foo with value 'bar'
-e                      |   Generate extended information for debugger/profiler
-f <`file`>             |   Parse and execute <`file`>.
-h                      |   This help
-i                      |   PHP information
-l                      |   Syntax check only (lint)
-m                      |   Show compiled in modules
-r <`code`>             |   Run PHP <`code`> without using script tags <?..?>
-B <`begin_code`>       |   Run PHP <`begin_code`> before processing input lines
-R <`code`>             |   Run PHP <`code`> for every input line
-F <`file`>             |   Parse and execute <`file`> for every input line
-E <`end_code`>         |   Run PHP <`end_code`> after processing all input lines
-H                      |   Hide any passed arguments from external tools.
-S <`addr`>:<`port`>    |   Run with built-in web server.
-t <`docroot`>          |   Specify document root <`docroot`> for built-in web server.
-s                      |   Output HTML syntax highlighted source.
-v                      |   Version number
-w                      |   Output source with stripped comments and whitespace.
-z <`file`>             |   Load Zend extension <`file`>.
&nbsp;                  |   &nbsp;
args...                 |   Arguments passed to script. Use -- args when first argument starts with - or script is read from stdin
&nbsp;                  |   &nbsp;
--ini                   |   Show configuration file names
&nbsp;                  |   &nbsp;
--rf <`name`>           |   Show information about function <`name`>.
--rc <`name`>           |   Show information about class <`name`>.
--re <`name`>           |   Show information about extension <`name`>.
--rz <`name`>           |   Show information about Zend extension <`name`>.
--ri <`name`>           |   Show configuration for extension <`name`>.

# Misc functions

Function | Description
--- | ---
filter_input | get the specific external variable by name and filter it

# Misc 2

    <<< EOF

It is called `heredoc`.

# PHP Associative Arrays

Associative arrays are arrays that use named keys that you assign to them.

There are two ways to create an associative array: 

    $age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");

or:

    $age['Peter'] = "35";
    $age['Ben'] = "37";
    $age['Joe'] = "43";

The named keys can then be used in a script:

Example
    <?php
    $age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");
    echo "Peter is " . $age['Peter'] . " years old.";
    ?>

Loop Through an Associative Array

To loop through and print all the values of an associative array, you could use a foreach loop, like this:

Example

    <?php
    $age = array("Peter"=>"35", "Ben"=>"37", "Joe"=>"43");

    foreach($age as $x => $x_value) {
    echo "Key=" . $x . ", Value=" . $x_value;
    echo "<br>";
    }
    ?>

# good shortcuts

    <?= CodeIgniter\CodeIgniter::CI_VERSION ?>

equivalent to

    <?php echo CodeIgniter\CodeIgniter::CI_VERSION ?>

### misc

You don't typically need to do this, since PHP will coerce the type for you in most circumstances. For situations where you do want to explicitly convert the type, cast it:

    $num = "3.14";
    $int = (int)$num;
    $float = (float)$num;



<br><br><br><br><br><br><br><br>

## References
* https://www.w3schools.com/php/
* https://www.stackoverflow.com/
* https://www.php.net/manual/en/features.commandline.options.php
* https://www.php.net/manual/en/language.types.string.php
* https://www.w3schools.com/php/php_file_open.asp
* https://www.w3schools.com/php/func_math_mt_rand.asp
* https://www.w3schools.com/php/php_looping.asp
* https://www.w3schools.com/html/html_forms.asp
