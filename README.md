# jQuery Facebook Helper

This is a simple jQuery plugin that helps you add the Facebook Javascript SDK to your site asynchronously. It also allows you to to use jQuery events to run code before and after the Facebook's code is initialized.

To add the Facebook Javascript SDK to your site simply call the following Javascript somewhere in your document:

```javascript
$(document).fb('youappid');
```

If you want to use the events simply add handles to either the fb:initializing or fb:initialized events.

```javascript
$(document).on('fb:initializing', function() { 
  // Do something before FB.Init is called
});

$(document).on('fb:initialized', function() {
  // Do something after FB.Init is called
});
$(document).fb('youappid');
```

The benefit of this library is that it you can add the initialization code in a single place in your app (such as a layout or master page) and then use the jQuery events to run the appropriate code on specific pages. For example, on your login page you may want to do something like this:

```javascript

$(document).ready(function() {
  // Add the function to run after FB is initialized
	$(document).on('fb:initialized', function() {
	  FB.getLoginStatus(fbAuthStatusChange);
	});
	$(document).fb('youappid');
});

function fbAuthStatusChange(request) {
	// Do something
}
```

