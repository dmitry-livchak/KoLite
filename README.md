# KoLite
**KoLite** KoLite contains a set of helpers to aid in creating MVVM applications using JavaScript and Knockout.


## Current Version
1.0.1


## Quick start
### asyncCommand 
<pre>
&lt;button data-bind="command: loadCmd">Save&lt;/button>
</pre>
<pre>
saveCmd = ko.asyncCommand({
	execute: function(complete) { ... }
})
</pre>

### asyncCommand and Activity
<pre>
&lt;button data-bind="activity: saveCmd.isExecuting, command: saveCmd">Save&lt;/button>
</pre>

<pre>
saveCmd = ko.asyncCommand({
	execute: function(complete) { ... },
	canExecute: function(isExecuting) {
            return !isExecuting && self.isDirty() // your own flag to check if you should save or not
        }
})
</pre>

### dirtyFlag
<pre>
// Your model
var Person = function () {
	var self = this;
	self.id = ko.observable();
	self.firstName = ko.observable().extend({ required: true });
	self.lastName = ko.observable().extend({ required: true });
	self.dirtyFlag = new ko.DirtyFlag([self.firstName,self.lastName]);
	return self;
};
</pre>

Hook these into your viewmodel ...

<pre>
//Did It Change?          
viewModel.dirtyFlag().isDirty();
</pre>

<pre>
//Resync Changes
viewModel.dirtyFlag().reset();
</pre>


## Authors

**Hans Fjällemark**

+ http://twitter.com/hfjallemark

**John Papa**

+ http://twitter.com/John_Papa

## Credits
Inspired by http://KnockoutJS.com


## Copyright

Copyright © 2012 [Hans Fjällemark](http://twitter.com/hfjallemark) & [John Papa](http://twitter.com/John_Papa).

## License 

toastr is under MIT license - http://www.opensource.org/licenses/mit-license.php