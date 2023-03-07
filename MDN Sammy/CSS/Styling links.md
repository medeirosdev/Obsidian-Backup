tags: #css 

###### link states
- `:link` -> a link that has a destination (i.e., not just a named anchor), styled using the `:link` [[Pseudo-classes and pseudo-elements#^3bb6e2|pseudo class]]
- `:visited` -> a link that has already been visited (exists in the browser's history)
- `:hover` -> a link that is hovered over by a user's mouse pointer
- `:focus` -> a link that is focused
- `:active` -> a link that is activated (e.g., clicked on)
###### styling some links
- The `pseudo-class` order is important because link styles build on one another
- The order is **L**o**V**e **F**ears **HA**te
``` css 
a{}
a:link{}
a:visited{}
a:focus{}
a:hover{}
a:active{}
```