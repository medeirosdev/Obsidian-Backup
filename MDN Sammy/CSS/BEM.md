tags: #css 
- BEM: _Block Element Modifier_
- a CSS naming convention, naming system

>[!warning] Avoid hierarchy
>use `user__icon` instead of `user__data__icon`
---
- **block**: a self-contained element in a page. Like a nav bar or a card
- **element**: a component that is part of a **block**. In a card it could be the the _title_ container or the _user name_ container
- **modifier**: like the name implies, it is a class that is used for a specific kind of a already established element, for example a premium card or a dark mode version of a card
---
- use a plain name for the **block**
- use the plain name along two underscores with the **element** name:
	- `user` -> block name
	- `user__profilePhoto` -> element name
	- `user__description` -> element name
- use two hiphens for the modifiers
	- `user` -> block name
	- `user--premiumMember` -> modifier
	- `user--basicMember` -> modifier

``` html

 <div class="user"> <!--- user block-->
   <img class="user__photo"> <!-- user photo element-->
   <div class="user__name">Name</div>
</div>
```