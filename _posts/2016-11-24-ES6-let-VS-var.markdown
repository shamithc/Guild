---
layout: post
title:  "ES6: let VS var"
date:   2016-11-11 16:23:47 +0530
categories: jekyll update
meta: "JavaScript"
---


Main difference between Let and Var is Scoping.


let is used to declare variables that are limited to block in which they are defined. Whereas var is used to define variable globally within defined function regardless of block scope.


Let us go through detailed examples,

### Case 1 - Global scope

{% highlight javascript %}
	var a = 'Global-Var';
	let b = 'Global-let';

	console.log(a); 	// Print 'Global-Var'
	console.log(b); 	// Print 'Global-let'
{% endhighlight %}


### Case 2 - Block Scope

{% highlight javascript%}

	// var function

	function varFn(){
		var x = 'scope - inside function';
		if (true){
			var x= 'scope - inside IF'
		}

		console.log(x); // scope - inside IF
	}


	// let function

	function letFn(){
		let x = 'scope - inside function';
		if (true){
			let x= 'scope - inside IF'
		}

		console.log(x); // scope - inside function
	}

{% endhighlight %}


### Case 3 - Redeclaring variables within a block

let will raise *SyntaxError* if redeclare variables within a block


{% highlight javascript%}

	function letFn(){
		let x = 10;
  		let x = 11;
		return("Done")
	}

  letFn(); //  Uncaught SyntaxError: Identifier 'x' has already been declared

{% endhighlight %}


### Case 4 - Declare variable before used

let will raise *ReferenceError* if referencing a variable before declared within a block

{% highlight javascript%}

	// letFn
	function letFn(){
		console.log(x); // ReferenceError: x is not defined
		let x = 10;
	}
	letFn();

	//varFn
	function varFn(){
		console.log(x); // undefined
		var x = 10;
	}
	varFn();

{% endhighlight %}

