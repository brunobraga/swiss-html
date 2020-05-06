# swiss-html
A Simple Web-browser Split Screen

The motivation behind this is to open multiple web pages in full-screen mode under a single browser. This is great for very large monitors, displays or TVs (e.g. 75-inch ones).


### The problem

Using the existing split functionality from Windows (or other operating systems), you will still lose a considerable real estate of the screen because of the browser elements (tabs, address bar, etc). If you go full-screen, the current browser window takes the entire space (currently there is no functionality to limit the scope of the fullscreen to the split screen size only).

This is the result:

![bad](https://github.com/brunobraga/swiss-html/blob/master/docs/bad.jpg?raw=true)

### The solution

By far not the most elegant, but incredibly simple to deliver: use frames within a webpage and maximize the single page browser.
This way every screen in the split screen page gets the feeling of a full screen.

This is very useful if you have a very large display and want to make the most of it by placing more information (multiple sites, reports, dashboards, etc).

This is the result:

![good](https://github.com/brunobraga/swiss-html/blob/master/docs/good.jpg?raw=true)


## How to Use

A simple guide on how to use this template for displaying multiple web pages on a large monitor device with the split-screen feeling.

### Step 1 - Configuration

Copy the `template.html` file, save on a local computer or sever, and configure the Javascript variables:

#### TITLE

```
    /*
    The page title that is displayed by the web browser.

    @type {string}
   */
    var TITLE = 'Simple Web-browser Split Screen';
```

TBD...