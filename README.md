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

This is supposed to serve just as a template, instead of an installable script/application. Start from the template, configure as you see fit, and load to whatever device you need to. That simple!

### Configuration

Copy the `template.html` file, save on a local computer or sever, and configure the Javascript variables:

#### TITLE

```
    /*
    The page title that is displayed by the web browser.

    @type {string}
   */
    var TITLE = 'Simple Web-browser Split Screen';
```

Change this to whatever you like.

#### COLUMNS

```
    /*
    The number of columns for the split screen.

    Note: The total number of cells in the split screen matrix (frameset) is defined by `ROWS` x `COLUMNS`. 
          So keep in mind:

      - value should be an integer number higher than 0 (zero)
      - the larger the number, the smaller the space available to load a page (some sites will be responsive 
        to space, which might change the expected experience - if you need this, consider changing the browser 
        **zoom** settings)

    @type {number}

    @seealso `ROWS`
    */
    var COLUMNS = 2;
```

Change this with attention to the documentation above.


### ROWS

```
    /*
    The number of rows for the split screen.

    Note: The total number of cells in the split screen matrix (frameset) is defined by `ROWS` x `COLUMNS`.

      - value should be an integer number higher than 0 (zero)
      - the larger the number, the smaller the space available to load a page (some sites will be responsive 
        to space, which might change the expected experience - if you need this, consider changing the browser 
        **zoom** settings)
        
    @type {number}

    @seealso `COLUMNS`
    */
    var ROWS = 2;
```

Change this with attention to the documentation above.

### DATASET

```
 /*
    The main dataset used to load the frames on screen in a split screen style.

    @property {string} url
                  the URL address to point a particular frame to.
                  Note: watch out for browser security settings, such as X-Frame-Options, 
                        or loading issues with the server, which impact the frame output

    @property {number} refresh
                  determines the rate of refresh, in seconds, forced by this page.
                  Use zero (0) for no refresh. 
        
    @property {number} frame
                  determines the frame number to which you want the URL to be always displayed on.
                  Note: You can only set a single fixed frame in this dataset.
                  Use negative one (-1) to ignore fixing the URL to any particular frame.
                  In this case, if a frame has no fixed URL, it will randomly select any of '-1' available.
                  If you combine the REFRESH property with this, you will get an experience that every X seconds
                  the website may be a different one (random).

                  Frame position numbers are described below (R - rows, C - columns):
                  |-----------|-----------|------------|---------------|
                  | 0*R+0     | 1*R+0     | ..*R+0     | (C-1)*R+0     |
                  | 0*R+1     | 1*R+1     | ..*R+1     | (C-1)*R+1     |
                  | 0*R+..    | 1*R+..    | ..*R+..    | (C-1)*R+..    |
                  | 0*R+(R-1) | 1*R+(R-1) | ..*R+(R-1) | (C-1)*R+(R-1) |
                  |-----------|-----------|------------|---------------|

                  See the function `checkFrameSetup` for a representation of this output based on your 
                  specified settings.

    @type {Array.{}}

    */
    var DATASET = [
      { 'url': ..., 'refresh': ..., 'frame': ... },
      { 'url': ..., 'refresh': ..., 'frame': ... },
      ...
    ];
```

Change this with attention to the documentation above.

To check the naming of the frames, you can use the formula above, or just call the function `checkFrameSetup()` from the developer tools within your browser, which should produce something like this:

_(example if you set ROWS=10, COLUMNS=10)_

![checkFrameSetup](https://github.com/brunobraga/swiss-html/blob/master/docs/checkFrameSetup.png?raw=true)

Of course the result isn't great if you do not have enough real estate for so many windows... The code, however, is designed to do it if you want to.

![10x10](https://github.com/brunobraga/swiss-html/blob/master/docs/10x10.jpg?raw=true)


### Issues

#### Content Security Policy Violation

Most websites nowadays block the rendering of the page if you are under a frame. Some services may offer workarounds or functionality designed for this purpose (e.g. Youtube with the `embed` tag), so it's up to you to deal with these issues depending on what content you want displayed. 

I initially designed this for internal purposes only, so this is a problem I do not really have. If you encounter this, check online for potential solutions (there are plenty). Start from the console output errors and search for the specific header responses from the web page you are trying to open.

### What's Next

#### Application

A next stage of this would be a better scripted solution that could handle a number of other dependencies to get this fully automated on large monitors or displays, such as:
- restart of browser on crashes
- auto load with specific settings as soon as the user logs in (this is a very typical scenario if the user is the TV or large monitor locked on the wall)
    - consider multi display scenarios
    - consider altering zoom for better visual experience of the display
- schedule display auto-lock/unlock

I did not researched the above in much detail, there might be a solution out there solving this already. Let me know!


## Contribute

Just fork this code, create an issue, and we take it from there!
