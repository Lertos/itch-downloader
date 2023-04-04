# The SUPER-ULTIMATE-ITCH.IO-BUNDLE-DESTROYER-2000
<br />

## PURPOSE
I guess spam-downloading is a real issue on Itch.. so they have no way to mass download files - which sucks if you buy a big bundle...
<br />

## HOW TO
This isn't a whole lot quicker, but does save a ton of clicks.
<br />
**NOTE**: You could also speed it up more by making a marco that does steps 
<br />

1. Login and open the bundles page on itch.io (https://itch.io/my-purchases/bundles)
2. Click the bundle you want to download
3. Press F12 and navigate to the console tab. Paste the below code into the console and press Enter
4. Now it will open all pages for you, 1 second at a time. (You can try decreasing "1000", but they do have a "Too Many Requests" buffer so be careful)
5. Start at the most-left tab and you can hover your mouse over the "Download" button, click it, and press CTRL+TAB to go to the next tab
6. Repeat steb 5 over and over (this is where a marco would be useful)
<br />
<br />

```
$(document).ready(function() {
	//Need to be on bundle page
	if (window.location.href.indexOf('https://itch.io/bundle/download/') != 0) {
		alert("You must be on a page that starts with: https://itch.io/bundle/download/");
		return;
	}
	
	var downloadButtons = $('a.button.game_download_btn');
	
	if (downloadButtons.length == 0) {
		alert("There are no download buttons on this page")
		return;
	}
	
	var count = downloadButtons.length - 1;
	var openInterval = setInterval(openLink, 1000);
	
	function openLink() {
		if (count == 0)
			clearInterval(openInterval);
			
		downloadButtons.get(count).dispatchEvent(new MouseEvent("click", {ctrlKey: true}));
		count--;
	}
});
```
