Testing (Incomplete)
===================


##Why?

Testing is a good idea for at least 3 reasons.

* Writing tests before you write code means you can (ideally) stop bugs from entering the codebase, or at the very least, catch them early on in the process.
* Tests allow you to refactor in the confidence that you're not inadvertedly breaking something in the codebase.
* By their nature, tests can be used as a rudimentary form of documentation.


##Javascript Testing

[Jasmine](http://jasmine.github.io/) is a good tool to use because it is widely used, well documented and is in active development.

Watching the videos in [this playlist](https://www.youtube.com/watch?v=Si59RlSqDQ0&list=PLOxOmO43E6Jt0SruKGxtZs-W3PJN90G_a) will fill you in on how to create and run a test suite. Once you've watched the first few videos, you can clone the [Javascript Koans repo](https://github.com/mrdavidlaing/javascript-koans) and work through the examples.

Working on isolated examples is all very well, but writing tests for real world javascript does need a bit of thought.



Here are some rules of thumb to keep in mind, paraphrasing heavily from [this article](https://shanetomlinson.com/2013/testing-javascript-frontend-part-1-anti-patterns-and-fixes/) by Shane Tomlinson. 

* Don't inline javascript, as it is can't be tested.
* If a function is longer than 10 lines, it's very likely doing too much.
* All code should have a public interface, like in an object literal or in the [Module Pattern](https://css-tricks.com/how-do-you-structure-javascript-the-module-pattern-edition/).

#### Object Literal

	var personObjLit = {
		ssn: '1234567',
		age: 30,
		name: 'Joe Bloggs',

		getAge: function(){
			return this.age;
		},

		getName: function(){
			return this.name;
		} 
	}

#### Module Pattern

	var personMod = (function() {

		// private variables
		var ssn = '1234567'; 
		var age = 30;
		var name = 'Joe Bloggs';

		//exposed to public
		return {
			getAge: function(){
				return age;
			},

			getName: function(){
				return name;
			} 
		}
	})();

Keen not to overcomplicate things, do bear in mind the following: 

>"Whilst the module pattern is useful for many things,
>if you find yourself not requiring specific properties
>or methods to be private, the object literal is a more
>than suitable alternative."

Additionally, 

> a drawback to the Module pattern is "the inability to create automated unit tests for private members."
> A function that is not directly accessible cannot be directly tested. A tension exists in module design between keeping
> members private and exposing members to the public.


###Reading List
* http://alistapart.com/article/writing-testable-javascript
* http://addyosmani.com/resources/essentialjsdesignpatterns/book/
* https://shanetomlinson.com/2013/testing-javascript-frontend-part-1-anti-patterns-and-fixes/
* https://shanetomlinson.com/2013/writing-testable-javascript-part-2-refactor-away-anti-patterns/
* Book: http://jstesting.jcoglan.com/
* Screencast course http://www.letscodejavascript.com/