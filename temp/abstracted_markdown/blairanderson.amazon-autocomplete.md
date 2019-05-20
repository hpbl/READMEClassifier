# Amazon Autocomplete JS Plugin

AmazonAutocomplete is a vanilla JavaScript plugin to unlock the full power of the Amazon autocompletion engine right into your search input. 

**Demo** : @abstr_hyperlink 

@abstr_image 

## Installation

You can just grab the minified file from `/dist` or unminified from `/src` but I highly recommend installation through npm. 

@abstr_code_section 

If you think npm is just so @abstr_number or just feeling hipster, you can install it using @abstr_hyperlink as well:

@abstr_code_section 

Now add it to your html file:

@abstr_code_section 

## Usage

Create a text input in your html file for the search field.

@abstr_code_section 

Edit your main JavaScript file to create an AmazonAutocomplete instance with your search field CSS selector.

@abstr_code_section 

Now you got a search field on steroids. Go ahead and apply some styles to make it shine.

## Styling

This is a pretty lightweight JavaScript library so it applies just a few styles to some elements to make it work. You can apply your own styles and customize the look of all the components within the widget. If you’re not that much into CSS, you can grab the following snippet and safely shot it into your stylesheet to get a decent default look. As you can see, AmazonAutocomplete goes all the way @abstr_hyperlink .

@abstr_code_section 

## Advanced Usage

### Configuration

You can customize the plugin behaviour by passing along a config object when instantiating AmazonAutocomplete. These are the properties you can specify:

#### `new AmazonAutocomplete([paramsObject])`

Param | Type | Required | Details \------------ | ------------- | ------------- | ------------- selector | `string` | Yes | CSS selector of the search field. delay | `integer` | No | The keyup event on the search field is debounced. This attribute will set the fire rate limit (in milliseconds) on the keyup event callback. Default: `@abstr_number` showWords | `boolean` | No | Enable/disable revealing of the words list panel. Can be useful if you want to show the suggested words on your own custom widget. Default: `true` hideOnblur | `boolean` | No | Indicates whether the words list panel should hide when the search field loses focus. Default: `true`

### Events

Each AmazonAutocomplete instance will fire some events. You can susbscribe to these events to, for example, save the selected word in your DB or to show suggested words in your own widget.

Event | Callback Param | Details \------------ | ------------- | ------------- onSelectedWord | `string` | This is event is fired when some of the following actions takes place: 

  * User clicks a word
  * User navigates through the words list and hits enter
  * User types keyword and hits enter (no suggested word selected)

The callback function will be called with the selected word as its only argument. onNewWords | `array` | This is event is fired when there are new suggested words available. It mostly happens when the keyup event fires on the search field. Keep in mind that the keyup is debounced to improve performance. 

### Advanced usage example

The next snippet shows how to initialize a AmazonAutocomplete with a @abstr_number ms debounce limit, not showing the words panel and not hiding on input text blur. As the words won’t show in the dropdown panel we’ll have to shown them in a custom panel.

@abstr_code_section 

## Features

  * **Size** : @abstr_number . @abstr_number kb. Goes down to @abstr_number . @abstr_number kb when gzipped.
  * **Browser support** : Amazon Autocomplete is supported by all major browsers and +IE @abstr_number . I don’t have any plans to ever support IE @abstr_number on any of my projects.
  * **Library Agnostic** : This plugin is all about vanilla JavaScript. No jQuery required. You can use it in any of your projects whether you’re working on Angular, React, Vue, or plain JavaScript.
  * **JSONP** : Yep. Amazon Autocomplete uses JSONP to fetch the data from Amazon. Requests are not being made via XHR because of the same-origin policy. Fortunately, the Amazon autocompletion endpoint is JSONP enabled so we can bypass this restriction.
  * **Multiple instances** : You can have multiple search fields in the same page all of them powered with Amazon Autocomplete. Don’t worry about setting different callbacks when fetching the Amazon autocompletion endpoint. Just create a new instance for each search field and this plugin will automagically handle everything for you. How cool huh?
  * **Keyup debounced** : With great power comes great responsibility. You don’t want to execute a GET request each time the user types a character and overload the Amazon autocompletion engine server. Amazon Autocomplete debounces the keyup event so that it will request new words only if some time has passed since last request. This is called @abstr_hyperlink . 



## Licence

AmazonAutocomplete is licensed under @abstr_hyperlink .
