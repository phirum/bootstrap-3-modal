bootstrap-3-modal
=================
A Meteor package making it easy to use bootstrap 3 modals in Meteor.

**Note 1:** In order for this package to work, you must include bootstrap 3 in
your meteor project. You can add bootstrap 3 to your project by adding the
package `mizzao:bootstrap-3`:

```
meteor add mizzao:bootstrap-3
```

This package does not include `mizzao:bootstrap-3` automatically (in case you
have included bootstrap 3 in another way).

Include this package with:

```
meteor add peppelg:bootstrap-3-modal
```

Usage
-----
To define your own modals, simply define new templates containing your modals
(**important**: your modals must have the class `modal`):

```html
<template name="exampleModal">
	<div class="modal fade">
		<div class="modal-dialog">
			<div class="modal-content">
				
				<div class="modal-header">
					<h4 class="modal-title">Modal example</h4>
				</div>
				
				<div class="modal-body">
					<p>A modal example.</p>
				</div>
				
				<div class="modal-footer">
					<button type="button" class="btn btn-default" data-dismiss="modal">Close</button>
				</div>
				
			</div>
		</div>
	</div>
</template>
```

Modal templates can be used as ordinary templates in Meteor (`created`,
`helpers`, `rendered`, `events` and `destroyed` all works as you're used to).

No modal is shown (or even inserted into the DOM) by default. By calling
`Modal.show(<templateName>)`, the modal is inserted into the DOM and shown.

```javascript
Meteor.startup(function(){
	// Show the example modal 3 seconds after startup.
	setTimeout(function(){
		Modal.show('exampleModal')
	}, 3000)
})
```

If a second argument is passed to `Meteor.show`
(`Meteor.show(<templateName>, <dataContext>)`), it will be used as the data
context for the template (works as the `data` parameter for
[Template.dynamic](http://docs.meteor.com/#/full/template_dynamic)).

The modal can be removed by calling `Modal.hide()` (or by using the other ways
to remove modals in bootstrap).

Examples
--------
At the moment there is one sign up modal and one sign in modal in the directory
`examples`. When a proper way to do this in Meteor (settings min password
length, and things like that) existst in Meteor, I will probably create a
package like accounts-ui, but with modals instead.