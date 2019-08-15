*Note*: The 1.0 release requires PHP > 7.1.

# Description
Fork from HumanNameParser.php origninally by Jason Priem <jason@jasonpriem.com> and @davidgorges. Takes human names of arbitrary complexity and various wacky formats like:

* J. Walter Weatherman 
* de la Cruz, Ana M. 
* James C. ('Jimmy') O'Dell, Jr.
* Dr. James C. ('Jimmy') O'Dell, Jr.

and parses out the:

- leading initial (Like "J." in "J. Walter Weatherman")
- first name (or first initial in a name like 'R. Crumb')
- nicknames (like "Jimmy" in "James C. ('Jimmy') O'Dell, Jr.")
- middle names
- last name (including compound ones like "van der Sar' and "Ortega y Gasset"), and
- suffix (like 'Jr.', 'III')
- title (like 'Dr.', 'Prof') *new*


# How to use

```php
use HumanNameParser\Parser;

try {
	
	$nameparser = new Parser();
	$name = $nameparser->parse("Alfonso Ribeiro");

	echo "Hello " . $name->getFirstName();
	echo "Hello " . $name->getLeadingInitial();
	echo "Hello " . $name->getFirstName();
	echo "Hello " . $name->getNickNames();
	echo "Hello " . $name->getMiddleName();
	echo "Hello " . $name->getLastName();
	echo "Hello " . $name->getSuffix();
	
} catch(HumanNameParser\Exception\FirstNameNotFoundException $e) {
	// catch body
} catch(HumanNameParser\Exception\LastNameNotFoundException $e) {
	// catch body
}
```

# Tests

```sh
composer test
```
