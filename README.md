## Website Performance Optimization portfolio project

Your challenge, if you wish to accept it (and we sure hope you will), is to optimize this online portfolio for speed! In particular, optimize the critical rendering path and make this page render as quickly as possible by applying the techniques you've picked up in the [Critical Rendering Path course](https://www.udacity.com/course/ud884).

To get started, check out the repository and inspect the code.

### Getting started

#### Part 1: Optimize PageSpeed Insights score for index.html

Some useful tips to help you get started:

1. Check out the repository
1. To inspect the site on your phone, you can run a local server

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to the top-level of your project directory to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ./ngrok http 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights! Optional: [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)

Profile, optimize, measure... and then lather, rinse, and repeat. Good luck!

#### Part 2: Optimize Frames per Second in pizza.html

To optimize views/pizza.html, you will need to modify views/js/main.js until your frames per second rate is 60 fps or higher. You will find instructive comments in main.js. 

You might find the FPS Counter/HUD Display useful in Chrome developer tools described here: [Chrome Dev Tools tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks).

### Optimization Tips and Tricks
* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>

### Customization with Bootstrap
The portfolio was built on Twitter's <a href="http://getbootstrap.com/">Bootstrap</a> framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* <a href="http://getbootstrap.com/css/">Bootstrap's CSS Classes</a>
* <a href="http://getbootstrap.com/components/">Bootstrap's Components</a>

11/16/17
https://www.youtube.com/watch?v=JJceDx4-Kr4 --didn't help much
had to generate the local server using the command "python -m http.server 8080"

11/17/17
ok, finally figured out how to get the pageSpeed insights data

Open node.js prompt
* "python -m http.server 8080"
* put ngrok in file directory
Open a separate node.js command prompt
* "ngrok http 8080"
* put ngrok https url into https://developers.google.com/speed/pagespeed/insights/
Initial Results with the base code: 
Mobile 27/100
Desktop 29/100
Results are terrible, but it took me a while to figure out how to get the starting numbers. Key learning: I shouldn't have been trying it while at work, because the proxy settings were messing me up.

Next Step: Optimize Images
http://optimizilla.com/
Re-ran pageSpeed Insights
Mobile: 53/100
Desktop: 60/100

Commentary: Wow, crazy how a simple image compression can make such a huge difference!

Next Step: Optimize CSS Delivery
11/20:
Change the print.css to only be used when media="print"

11/18: Work on 60FPS for the pizza part
Starting FPS is around 30-40ms. Yikes!
Changed to use bootstrap instead of the style variable when generating pizza elements
the helped a little, now I'm around 20-25 FPS
Changed the variables in makeRandomPizza. We can use the same variable for all the for loops
Modify the changePizzaSizes for loop, don't want to access the offset width in every iteration of the loop
re-worked the resizePizza's code. Now that part is under 3ms. Still have to figure out why it's so high for generating the last 10 frames
re-factored the updatePositions code. 
Wow, now the scrolling is around 1ms!

11/20
ok, back to pageSpeed insights....
Found a code snippet on a better way to load the google font api, now my score is 62 for both mobile and desktop. Told me to optimize images, I thought I did that already. 
what?I optimized 2 images, and my pageSpeed insights score went to a 95 on mobile and 94 on desktop?

11/21 - 
Restored code in updatePositions so that pizzas move during scrolling

To use the site: 
* Launch the index.html from the root directory
* To access the pizza page, click on the link which says "Cam's Pizzeria"
* Scroll down and look for the sliding bar. Changing the setting on this bar will change the size of the pizzas displayed on the screen
