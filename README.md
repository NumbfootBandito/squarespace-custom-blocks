Squarespace Custom Blocks
=======

> A reference for customizing the markup of Squarespace's system blocks in a Developer mode template.

> Note: This is an undocumented feature of Squarespace and could become deprecated in the future.



## Overview
Squarespace's backend CMS is unique in that it allows a user to lay out content using a drag and drop block system that Squarespace calls LayoutEngine. If you're familiar with [Squarespace Developer mode](http://developers.squarespace.com), you'll know that you can build a completely custom web template to meet the needs of your intended design. You also get some flexibility in customizing the CMS UI. For instance the following items are under your control:

* [Navigations](http://developers.squarespace.com/menus-navigation/)
* [Collections](http://developers.squarespace.com/collections/)
* [Page Layouts](http://developers.squarespace.com/layouts-regions/)

This is a great feature of Squarespace's Developer mode, however a key content creation method in Squarespace are the LayoutEngine blocks. As of right now there isn't a way to create completely custom blocks, but there is a way to overwrite the block template of some of Squarespace's blocks.

**Disclaimer:** The only features that Squarespace officially supports are the ones in the official documentation. You're on your own here, and Squarespace may or may not change or deprecated the methods listed in this repo.



## Overwriting a Squarespace Block Template
Like I said above we can't create our own blocks, but we can overwrite some. I do not know the reason that some Squarespace blocks can be overwritten and some can't, but here's a list of all of Squarespace's blocks, with the restricted uneditable blocks noted. I've grouped them similar to how they're grouped in Squarespace.

### Basic
* *Text* - Locked
* *Markdown* - Locked
* Quote
* Image
* *Video* - Locked
* Audio
* *Embed* - Locked

### Gallery
* Slideshow
* Carousel
* Grid
* Stack

### Summary
* Wall
* Carousel
* List
* Grid

### More
* *Spacer* - Locked
* *Line* - Locked
* Form
* Newsletter
* *Map* - Locked
* *Code* - Locked
* Menu
* Calendar
* Opentable
* Bandsintown
* Album

### Filters & Lists
* Search
* Content Link
* Button
* Tag Cloud

### Commerce
* *Product* - Locked
* *Amazon* - Locked
* Donation

### Charts
* Bar Chart
* Line Chart
* Pie Chart

### Social Blocks
* *Twitter* - Locked
* *Foursquare* - Locked
* Social Links
* RSS
* *500px* - Locked
* *Instagram* - Locked
* *Flickr* - Locked
* *Soundcloud* - Locked

Currently there are 3 Squarespace blocks are use the same block template. Those three are Gallery, Summary and Chart blocks. Although they appear as 11 different blocks in the LayoutEngine UI, there's only 3 block templates.



## Installation
The easiest way to install a template into your Squarespace Developer mode template is to clone this repo and move the block template and configuration file into your template's `blocks` folder.

### How It Works
The way Squarespace handles these custom block templates is quite simple. Like [custom collections](http://developers.squarespace.com/collections/), you'll need to create a configuration file, and then a template. In my testing, the file name of the template is irrelevant, but the block name specified in the configuration is important. So the two files you'll need are:

* yourblockname.block.conf
* yourblockname.block

#### The configuration file

Your configuration file is going to look like this:

```
{
    "type": "image"
}
```

The `type` is the name of the Squarespace system block you are overwriting. There's not an easy way to know what the Squarespace system block types are. The way you can find out a block type name is by adding that Squarespace block to your template, then using your browser DevTools to examine the markup. The block type is usually printed into the HTML. The good news is we'll keep a reference list in this repo. :)

#### The template

Now that you've specified the system block you wish to overwrite, you then have to create a template. As with any development on Squarespace, console logging the current index JSON will print out the available JSON in these blocks. So add a `console.log( {@|json-pretty} );` to your block template, then head into the backend UI and add that block type to a test page. After that, your console should be printing the available JSON in that particular block type.

## Disclaimers

Use custom block templates with caution. This is undocumented and unofficial, so it's of course not supported by Squarespace. Don't be shocked if at some point in the future Squarespace deprecates or disables this feature.