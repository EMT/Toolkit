Javascript Best Practices
=========================

During the course of building sites, it occasionally becomes apparent that certain methods of 
doing things can cause issues down the line. This document helps us keep a record of such things,
so we can improve our workflow in the future.

###Always decouple CSS and javascript selectors

Imagine you have an element that is associated with some javascript interactivity. Let's say, a big red button that adds a product to a cart on click.

In code, we could have the following HTML&hellip;

    <div class='add-to-cart'>Add to cart</div>
    
&hellip;CSS&hellip;

    .add-to-cart{
    	background:red;
    	height:100px;
    	width:200px;
    }

&hellip; and Javascript&hellip;

	$(".add-to-cart").click(function(){
		//code to add product to cart goes here...
	});


Later on, you may decide you want another element to have the same javascript interactivity. But you want it to be a simple text link instead.
If you add the class `add-to-cart` to the element, it will take on the javascript functionality, but it will also gain an appearance that
you don't want it to have.

The solution is to make sure all selectors are used by either *CSS only* or *javascript only*. A simple way to help you stick to this is to prefix
all selectors used by javascript with `js-`.

So in the example above, the code will become:

    <div class='add-to-cart js-add-to-cart'>Add to cart</div>
    
<!-- -->

    .add-to-cart{
    	background:red;
    	height:100px;
    	width:200px;
    }

<!-- -->

	$(".js-add-to-cart").click(function(){
		//code to add product to cart goes here...
	});


For further reading, head over to [philipwalton.com/articles/decoupling-html-css-and-javascript/](http://philipwalton.com/articles/decoupling-html-css-and-javascript/)