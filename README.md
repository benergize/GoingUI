# GoingUI
Powerful lightweight web UI framework for components, SPAs and whatever else. Write JavaScript, not framework.

## How do I start using GoingUI?
Add GoingUI to your project with `<script src = 'going-ui.js'></script>` and start using it by creating a new instance with `var gapp = new GoingUI()`.

## What's it for? When would I use it?
Let's say you're building a digital scrapbook. It's going to be filled with photos and text boxes with descriptions of the photos. There's a bunch of ways you could do this. You could write the HTML for one photo, then copy and paste it, but that will get messy on the page fast, and if you want to make a change to the format, you'll need to change it for each one. Let's say we want to do it with JavaScript, say, populating the photos on the page from JSON. Here's how you might do it in pure JavaScript.

```

	<div id = 'scrapbook'></div>
	
	<script>
		//Div to hold the photo and description
		let photoHolder = document.createElement("div");
		photoHolder.classList.add("photoHolder");

		//The image element for the photo
		let photo = document.createElement("img");
		photo.src = 'momsbirthday.png';
		photoHolder.appendChild(photo);

		//Description of the photo
		let desc = document.createElement("span");
		desc.innerHTML = "Picture of mom on her birthday.";
		photoHolder.appendChild(desc);

		//Add it to the scrapbook
		document.getElementById('scrapbook').appendChild('photoHolder');
	</script>
```

This works, but it's a lot of code to do something very simple. It gets even more complicated if we need to add styles, classes, ids, and anything else. This is where web frameworks come in, and GoingUI is one such framework. Why use GoingUI over, say, React? Because you want to write JavaScript, not React. Here are two ways you could acomplish the above using GoingUI.

1: JSON style
```

	<div id = 'scrapbook'></div>
	
	<script>
		//Register a component called 'photo'
		gapp.register("photo", {
			"element": `
				<div class = 'photoHolder'>
					<img class = 'photo' data-gofield = 'image'>
					<span class = 'desc' data-gofield = 'desc'></span>
				</div>
			`
		});

		//Add photo to the scrapbook with the properties filled in.
		document.getElementById('scrapbook').appendChild(
			gapp.create("photo", {
				"image": { "src": "momsbirthday.png" },
				"desc": { "innerHTML": "Picture of mom on her birthday." }
			}
		);
	</script>
```

2: HTML style
```
	<div id = 'scrapbook'></div>


	<div class = 'photoHolder' data-goui = 'photo'>
		<img class = 'photo' data-gofield = 'image'>
		<span class = 'desc' data-gofield = 'desc'></span>
	</div>
	
	<script>
		//Creates a component from the photo HTML element and removes it from the DOM.
		gapp.init();
		
		//Add photo to the scrapbook with the properties filled in.
		document.getElementById('scrapbook').appendChild(
			gapp.create("photo", {
				"image": { "src": "momsbirthday.png" },
				"desc": { "innerHTML": "Picture of mom on her birthday." }
			}
		);
	</script>
```

## Can GoingUI be used to create entire SPAs?

Yes, and it has been! But that documentation is coming soon.

## If I need help or want to tell the creator he's a jerk, who should I contact?

ben@benergize.com
