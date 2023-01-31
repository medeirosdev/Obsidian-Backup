tags: #html 
#### Metadata
##### Open Graph Data
**Open Graph Data** is a metadata protocol that _Facebook_ invented to provide richer metadata for websites. In the MDN Web Docs sourcecode, you'll find this:
``` HTML
<meta property='og:image' content='*url to a image*'>
<meta property='og:description' content='text describing the source content'>
<meta property='og:title' content='source title'>
```
##### Twitter Cards
Twitter also has a similar proprietary metadata protocol like [[HTML#Open Graph Data|Open Graph Data]], which has a similar effect when the site's URL is displayed on twitter.com
``` HTML
<meta name='twitter:title' content='Mozilla Developer Network'>
```
##### Adding FavIcon to HTML Pages
``` HTML
<link rel='icon' href='url.extension'>
```



#### Text Fundamentals
- `<em>` - Stress Emphasis
	- You can use it to stress certain words, subtly altering the meaning of what we are saying
	- `<p>I am <em>glad</em> you were not <em>late</em>.</p>`
* `<strong>` - Strong Importance
	* To emphasize important words. we tend to stress them in spoken language and bold tem in written language
	* `<p>This liquid is <strong> highly toxic</strong>.</p>`
- Italic, bold, underline
	HTML5 redefined `<b>`, `<i>` and `<u>` with new, somewhat confusing, semantic roles.
	It's only appropriate to use the tags mentioned above to convey a meaning traditionally conveyed with bold, italics, or underline when there isn't a more suitable element
	- `<i>` is used to convey a meaning traditionally conveyed by italic: **foreign words**, **taxonomic designation**, **technical terms**, a **thought**
	- `<b>` is used to convey a meaning traditionally conveyed by bold: **keyword**, **product names**, **lead sentence**


#### Links
```html
## reference link
https://github.com/mdn/learning-area/tree/main/html/introduction-to-html/creating-hyperlinks
```
- Moving down into subdirectories
	- `<a href='projects/index.html'>one directory down</a>`
- Moving back up into parent directories ^e1f492
	- if you wanted to include a hyperlink inside projects/index.html pointing to pdf/project-brief.pdf, you'd have to go up a directory level, then back down into the pdf directory. To go up a directory, use two dots - __..__ -
	- `<p>A link to my <a href='../pdfs/project-brief.pdf'>project brief </a> </p>`

	>[!note]- Note
	>You can combine multiple instances of these features into complex URLs, if needed, for example '../../complex/path/to/my/file.html'

##### Links Best Practices
###### Link Wording

- Don't say 'link' or 'links to' in link text -- it's just noise. Screen readers tell people there's a link. Visual users will also know there's a link, because links are generally styled in a different color and underline
###### Linking to non-HTML resources
- When linking to a resource that will be downloaded, streamed, or has another potentially unexpected effect, you should add clear wording to reduce any confusion
``` html
<p>
	<a href='url.pdf'>
	download the sales report (PDF, 10MB)
	</a>
</p>

<p>
	<a href='url' target='_blank'>
		Watch the video (stream opens in separate tab, HQ quality)
	</a>
</p>

<p>
<a href='game'>
	Play the car game (requires Flash)
</a>
</p>
```

- Also use the download attribute when linking to a download
- `<a href='gigantic enourmous url plus .exe' download='name_for_the_file.ex'>Download firefox for windows</a>`
##### E-mail Links
- This is done using the `<a>` element and the ****mailto:*** URL scheme.
Example:
```HTML
<a href='mailto:nowhere@mozilla.org'>
Send email to nowhere
</a>
```
###### Specifying Details
- Any standard mail header fields can be added to the `mailto` URL you provide
- The most commonly used of these are 'subject', 'cc', and 'body'

Example:
``` html
<a href='mailto:nowhere@mozilla.org?cc=name@rapidtables.com&bcc=name3@rapidtable.com&subject=The%20subject%20of%20the%20email%20&body=The%20body%20of%20the%20email'>
Send email with cc, bcc, subject and body
</a>

<!--
email ? cc = email & bcc = email & suject = text & body = text
->

```


#### Advanced Text Formatting
##### Description Lists
```html
<!---Example one--->
<dl>
<dt>Soliloquy</dt>
<dd>In drama, where a character speaks to themselves</dd>
<dt>Monologue</dt>
<dd>IN drama, where a character speaks their thoughts out loud to share them with the audience and any other character present</dd>
<dt>aside</dt>
<dd>In drama, where a character shares a comment only with the audience for humorous or dramatic effect</dd>
</dl>

<!--Example two--->
<dl>
	<dt>Milk</dt>
	<dd>A white beverage extracted from cow's breast</dd>
	<dt>Coffee</dt>
	<dd>A blackish/brownish beverage made from the coffee beans</dd>
	<dt>Juice</dt>
	<dd>A normally cold mixture of water and fruit juice</dd>
</dl>

```
##### Quotation
###### Block Quotation
If a section of block level content is from somewhere else, you should wrap it inside `<blockquote>` element to signify this, and include a URL pointing to the source of the quote inside `<cite>` attribute.
For example:
``` html
<blockquote cite='mozilla_site/blockquote'>
<p>
The <strong>HTML<code>&lt;blockquote&gt;</code>Element</strong>(or <em>HTML Block Quotation Element</em>) indicates that the enclosed text is an extended quotation.
</p>
</blockquote>
```
###### Inline Quotation
Inline quotations work in exactly the same way, except that they use `<q>` element
```html
<p>The quote element - <code>&lt;q&gt;</code> is <q cite='url_mozilla/q'>intended for short quotations that don't require paragraph breaks</q>
```
###### Citations
`<cite>` element
``` html
<p>According to the
<a href='url/blockquote'>
<cite>MDN blockquote page</cite>
</a>
</p>
```
##### Abbreviation

``` html
<p>
We use <abbr title='HyperText MarkUp Language'>HTML</abrr>, HyperText Markup Language</p>

<p>
I think <abbr title='Revered'>Rev.</abbr> did it in the kitchen
</p>

```

##### Contact Details
`<address>` element
``` html
<address>Chris Mills, Manchester,The Grim North, UK</address> 

<address> <p> Chris Mills <br/> 
Manchester <br/> 
The Grim North <br/> 
UK </p> 
<ul> 
<li>Tel:01234 567 890 </li> 
<li>Email:me@grim-north.co.uk</li> 
</ul> 
</address>
```
##### Superscript and Subscript
```html
<p>My birthday is on 25<sup>th</sup> of May 2001.</p>

<p>
Caffeine's chemical formula is C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub>

<p>
if x<sup>2</sup> is 9, x must equal 3 or -3
</p>
```

##### Computer Code
`<code>`: for marking up generic pieces of computer code.
`<pre>`: for retaining whitespace (generally code block).
`<var>`: for specially marking up variable names.
`<kbd>`: for marking up keyboard (and other types of) input entered into the computer.
`<samp>`:for marking up the output of a computer program.
``` html
<pre> 
<code>const p = document.querySelector('p'); para.onclick = function() { alert('Owww, stop poking me'); } 
</pre> 

<p> You shouldn't use presentational elements like <code>&lt;font&gt;</code> and <code>&lt;center&gt;</code> 
</p> 

<p> In the above JavaScript example, <var>para</var> represents a paragraph element. 
</p> 

<p>Select all the text with <kbd>Ctr</kbd>/<kbd>Cmd</kbd> + <kbd>A</kbd></p>

<pre> 
$<kbd>ping mozilla.org</kbd> 
<samp>PING mozilla.org (63.245.215.20):56 data bytes 64 bytes from 63.245.215.20: icmp_seq=0 ttl=40 time=158.233 ms </samp> 
</pre>
```

##### Marking Up Time and Date
- HTML provides the `<time>` element for marking up times and dates in a **machine-readable** format. Example:
``` HTML
<time datetime='2016-01-20'>20 January 2016</time>
```

Another options:
``` HTML

<!-- Standard simple date -->
<time datetime='2016-01-20'>20 January 2016</time>

<!---Just year and month -->
<time datetime='2016-01'>January 2016</time>

<!---Just month and day -->
<time datetime='01-20'>20 January</time>

<!-- Jyst time, hours and minutes-->

<time datetime='19:30'>19:30</time>

<!----Seconds and milliseconds --->
<time datetime='19:30:01.856'>19:30:01.856</time>

<!--- DATE AND TIME --->

<time datetime='2016-01-20T19:30'></time>

<!----Date and time with timezone offset ------>
<time datetime='2016-01-20T19:30+01:00'>7.30pm, 20 January 2016 is 8.30pm in France</time>

<!---Calling out a specific week number----->
<time datetime='2016-W04'>The fourth week of 2016</time>

```




