# PHP Reference

## Variables and Constants

### Defining Variables

### Types of Data

### Variable Scope

### Predefined Variables

### Variable-handling Functions

## For

## If-Else

## While

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

    define(name, value, true/false)

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



## References
* https://www.w3schools.com/php/
