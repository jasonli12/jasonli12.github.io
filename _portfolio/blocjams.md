---
layout: post
title: BlocJams
thumbnail-path: "img/blocjams.png"
short-description: BlocJams is a Spotify replica for searching and playing your favorite songs online.

---

{:.center}
![]({{ site.baseurl }}/img/blocjams.png)

## Explanation

BlocJams, a replica of Spotify, is a project I worked on during my study at Bloc. The objective of the project is allow me to practice and learn core programming skills, such as HTML/CSS, JavaScript, DOM scripting, jQuery and AngularJS.

## Problem

After going through a variety of tutorials and training material, BlocJams is the first course-led project that teaches me how to apply fundamental programming concepts to a building a web application.

## Solution

------

### *HTML and CSS*

To start off, BlocJams walked me through how to set up the structure of a basic HTML document and how to apply CSS styling to a page. This is static content that we want to display once the page loads. One key takeaway from this part of the course is how to partition content, whether it is through the use of `section` tags within a single HTML page or separate HTML and CSS files to contain different pages, sections or even styling specific to a page. This makes code our cleaner, easier to read and easier to debug.

This is what our landing page looks like before we started incorporating JavaScript:

![BlocJams Landing Page](/img/blocjams.png)

------

### *Media Queries*


One of the key features that BlocJams walked me through was how to adjust how content is displayed across devices of different screen sizes. I learned that with media queries, I can adjust what and how content is displayed based on conditionals. For example, in the code below, if the width of device screen exceeds 640px, I can have the font-size for the HTML page scale to 112% of the default font-size and have my selling points float to the left by adding a few CSS properties to the column class.

{% highlight javascript %}
@media (min-width: 640px) {
    html { font-size: 112%; }

    .column {
        float: left;
        padding-left: 1rem;
        padding-right: 1rem;
    }
}
{% endhighlight %}

As you can see below, with a smaller screen size, BlocJams scales the landing page to a cleaner view.

<div style="margin-left: 30%; margin-right: 30%;">
  <img src="/img/blocjams-landing-1.png" alt="Landing Page Mobile" width="400" style="text-align: center">
</div>

------

### *Diving into JavaScript and the DOM*


Now that we have laid out the basic structure and styling for BlocJams, the next part is to incorporate JavaScript to allow a user to interact with the web application. Through building BlocJams, I learned that JavaScript is very powerful in automating tasks and performing loops.

For example, as you can see below, instead of repeating the code each time for each song and hard-coding it in HTML, we can create a template that stores the HTML format for each song row and iterate over each song in the album through a loop.

{% highlight javascript %}
var createSongRow = function(songNumber, songName, songLength) {
    var template =
        '<tr class="album-view-song-item">'
    +   '   <td class="song-item-number" data-song-number="' + songNumber + '">' + songNumber + '</td>'
    +   '   <td class="song-item-title">' + songName + '</td>'
    +   '   <td class="song-item-duration">' + songLength + '</td>'
    +   '</tr>'
    ;

    return template;
}
{% endhighlight %}

 Through JavaScript, you can also add event listeners to initiate certain behavior based on how a user interacts with the application.

 If I had to say what was likely the biggest challenge in learning how to build BlocJams was understanding how to traverse the DOM. Conceptually, the DOM is not difficult to grasp, but understanding what the DOM selectors such as `document.querySelector()` or `document.getElementsByClassName` return as output and how to access and change the content is the tricky part. Often times, when I think I am accessing the content, it turns out I am referencing a node that I did not know existed or I am not using the selector correctly.

 This is where the learning truly happens and when I started to use `console.log` in my code. As a beginner, it is very easy to make syntax errors and not know where the problem really is when the desired output is not displaying. Through building BlocJams, I learned that by injecting `console.log` in various parts of your code, you can validate whether the inputs, outputs and types are correct. By doing so repeatedly, it helped immensely with debugging because it narrowed down on where the problem was.

------

### *Incorporating jQuery*


"Don't reinvent the wheel"

I hear this saying every now and then and this seems to be where jQuery comes into play. BlocJams introduced jQuery to me as a JavaScript library that simplifies many common functionalities. In comparison to vanilla JavaScript and DOM scripting, jQuery makes it much simpler and easier to access the DOM.

Here is an example of BlocJams, where we switched between plain JavaScript to jQuery:

*Plain JavaScript:*
{% highlight javascript %}
var collectionContainer = document.getElementsByClassName('album-covers')[0];
{% endhighlight %}

*jQuery:*
{% highlight javascript %}
var $collectionContainer = $('.album-covers');
{% endhighlight %}

jQuery is much more intuitive when it comes to accessing DOM elements and improves readability. However, although jQuery has its benefits, in general, it is slower than plain JavaScript because the entire jQuery library is loaded even though you may only need a small subset of what the library offers.

------

### *Moving to AngularJS*

BlocJams is now fully up and running. The next part of involves building the same application in AngularJS. In our initial implementation of BlocJams, we defined the structure of our page and utilized methods available to us through the jQuery library. In AngularJS, though, the framework is more or less defined and we are left to fill in the content. One aspect I enjoyed when learning to implement BlocJams through AngularJS is how you can add behavior such as event handlers directly to an HTML element.

------

## Conclusion

BlocJams was a great starting point in helping me understanding how different pieces like HTML/CSS, the DOM, and libraries like jQuery fit together to make a dynamic web application. Each part of the build explained concepts well, included external resources for supplemental learning and reinforced core concepts. Learning how to build the exact same application through AngularJS was rewarding as well. Looking ahead, I plan to add new features like the ones below, except this time it will not be course-led:

* Create custom playlists.
* Provide recommendations based on what other users who listen to the same songs listen to.
