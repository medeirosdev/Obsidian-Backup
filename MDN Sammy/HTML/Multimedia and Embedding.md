tags: #html

##### images in HTML
- Search engines also read image filenames and count them towards SEO. Therefore, you should give your image a descriptive filename; `dinosaur.jpg` is better than `img835.png`.
##### video and audio content
###### the `<video>` element
- The `<video>` element allows you to embed a video very easily
``` html
<video src='video_name.some_format' controls>
<p>
Your browser doesn't support HTML video. 
Here is a <a href='video_name.some_format'> link to the video</a> instead
</p>
</video>
```
- A more general-support form:
``` html
<video controls>
<source src='video_url.format_1' type='video/format_1'>
<source src='video_url.format_2' type='video/format_2'>
<p>You can't play this shit</p>
</video>

```
###### the `<audio>` element
- Usage example
``` html
<audio controls>
	<source src='viper.mp3' type='audio/mp3'>
	<source src='viper.ogg' type='audio/ogg'>
</audio>
```


###### displaying video text tracks

- To do so we use the **WebVTT** file format and the `<track>` element
-  **WebVTT** is a format for writing text files containing multiple strings of text along with metadatas such as the time in the video at which each text string should be displayed
- WebVTT file example:

``` webvtt
1
00:00:22.230 --> 00:00:24.606
This is the first subtitle.

2
00:00:30.739 --> 00:00:34.074
This is the second.
```

To get this displayed along with the HTML media playback, you need to:
1. Save it as a `.vtt` file.
2. Link to the `.vtt` file with the `<track>` element.
	- `<track>` should be placed within `<audio>` or `<video>`, but after all `<source>` elements
	- Use the `kind` attribute to specify whether the cues are **subtitles**, **captions**, or **descriptions**
	- Use `srclang` to tell the browser what language you have written the subtitles in
	- Add a `label` to help readers identify the language they are searching for
Example:
``` html
<video controls>
	<source src='example.mp4' type='video/mp4'>
	<source src='example.webm' type='video/webm'>
	<track kind='subtitles' src='subtitles_es.vtt' srclang='es' label='Spanish'>
</video>
```
##### responsive images
###### different sizes
- We can use two attributes - `srcset` and `sizes` - to provide several additional source images along with hints to help the browser pick the right one.
 ``` html
 <img
 srcset='img_name-480w.jpg 480w, img_name-800w.jpg 800w'
 sizes='(max-width:600px) 480px, 800px'
 src='img-name-800w.jpg'
 >					
```
- `srcset`
	- it defines the set of images we will allow the browser to choose between, and what size each image is. 
	- Syntax
		- An **image filename** 
		- A space
		- The **image's intrinsic width** in pixels
- `sizes`
	- it defines a set of media conditions and indicates what image size would be best to choose, when certain media conditions are true.
	- Syntax:
		- A **media condition** (`(max-width:600px)`)`
		- A space
		- The **width of the slot** the image will fill when the media condition is true (*480px*)
		- *The last slot width, which does not have a media condition, is considered to be the default one*

###### different resolutions

- You can allow the browser to choose a nicer image resolution
```html
<img
 srcset='img_name1.jpg, img_name2.jpg 1.5x, img_name3.jpg 2x'/>
```
##### using `<picture>` and `<source>`
- The `<picture>` element is a wrapper containing several `<source>` elements that provide different sources for the browser to choose from, _followed by the all-important_ `<img>` element
``` html
<picture>
	<source media='(max-width:799px)' srcset='img_name.jpg'>
	<source media='(min-width:800px)' srcset='img_name.jpg'>
	<img src='img_name.jpg' alt='default'>
</picture>
```


