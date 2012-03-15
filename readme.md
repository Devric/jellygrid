#Jelly

###About

**Only 1 kb** - Cross device column system ( I won't call it a grid systems ), for those who finds all the current grid systems out there are either **bloated (including classes uses) or not powerful** enough, you are at the right place.


This grid designed specifically for cross devices, though it only contains up to 6 columns.
But honesly, how many people find that more than 6 columns to be useful? For me? rarely… 

####Class List
	.half
	.third
	.fourth
	.fifth
	.sixth
	
	.device-show
	.device-hide
	
	.device-half
	.device-third
	.device-half-last
	.device-third-last

#####Sample
Here is an example of Jelly 2 and 6 column:

	<div class="half">
		<div></div>
		<div class="last"></div>
	</div>

	<div class="sixth">
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div></div>
		<div class="last"></div>
	</div>
	
Only requires to apply class to its container, and all next div child will become your columns, and they are fliud too! So you can define the width of your container, faking it as max-width.

#####Mobile!!
**Jelly** does only one media-query, for most of us, it's enough… **really is enough**. It basically make a change to every column when screen resize down to 801px wide. To me, i consider PAD sizes and desktop design is really similar, you would want to use media-query to do something else, such as changing the UI, instead of change the columns. And how many of you would really need to design for all three devices in every project? More likly to be just desktop and mobile right? Unless you need to build for pads specifically.


So when it gets below 801px, it becomes one column! **but with a few extra mobile candies**.

	.device-hide			// show on desktop only, hide at device
	.device-show			// show on device only, hide at desktop
	
	.device-full			// redefine the column to single
	.device-half			// redefine the column to two columns
	.device-third			// redefine the column to three columns
	
	.device-half-last		// re-apply cancellation of margin
	.device-third-last		// re-apply cancallation of margin
	
#####Sample
This redefines the first two column as two column, and last column as full width, or you can use device-hide to get rid of it.

	<div class="third">
		<div class="device-half"></div>
		<div class="device-half-last"></div>
		<div class="last"></div>
	</div>
	
Or you can hide and show something while maintainig the columns

	<div class="half">
		<div class="device-half"></div>         // half on desktop, half again for mobile
		<div class="device-hide"></div>	        // this already on half(desktop), hides on mobile
		<div class="device-half-last device-show"></div>   // this only shows on device, and set to half
	</div>

#####Be Creative
If you want to make the middle container to go to last on mobile with full width, **USE .LAST or define FLOAT**

	<div class="fourth">
		<div class="device-half" style="float:right"></div>
		<div style="float:left">
		<div class="device-half" style="float:right"></div>
		<div class="last"></div>
	</div>

#####Spans?
What about spans, and column sizes?? **Jelly** does not have spans like grids, like the one you see from other grid system, span-2, span-3 etc… really, what chance would you use every single one of those span/(push) classes? maybe just one or two, but these class takes up a few more kb in your css, eventually bloats up both your css and html

**But… BUT I need them** Take a look at my demo page `<style></style>` code in the html, if you need them, than you make them, just got to remeber that you can always re-use the .last and .device-(width) classes.

######TIP at making span
Use your browser inspector, eg: you want to joint 3 .fourth columns, inspect the .fourth > div, than do a rough calc, you don't need to be percentage perfect if you don't need to be, span width = (3 * div width) + 2 * (margin-right).

If you are using class and applied ontop of a .half->.sixth element, like what I did in the demo page, than you need to override it with !important, but i was just lazy, you shoud do it like in this structure, than you woudn't need to hack it with **!important**.

	.container 
		.half 
			div
			div
	
###Supports
* Chrome
* Safari
* Firefox
* IE 8 + ( no media-query on desktop, but should be sweet with wp7 Mango devices )
