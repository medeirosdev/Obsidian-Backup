tags: #css 
###### percentage margins and padding
- When you use margin and padding set in percentages, the value is calculated from the `inline-size` of the containing block.
- thid means you can have equal-sized margins and padding all around the box
###### min- and max- sizes
- a common use of `max-width` is to cause images to scale down if there is not enough space to display them at their intrinsic width while making sure they don't become larger than that width
	- if you were to set `width:100%` on an image, and its intrinsic width was smaller than its container, the image would be forced to stretch and become larger, causing it to look pixelated
	- if you instead use `max-width:100%`, and its instrinsic width is smaller than its container, the image will not be forced to stretch and become larger, thus preventing pixelation