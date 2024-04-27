# Portfolio Website

by [Sandra Spighel](https://www.linkedin.com/in/sandraspighel/) - [HotSauceNinja](https://github.com/HotSauceNinja)

![home](https://github.com/HotSauceNinja/portfolio_v2/blob/main/README_images/portfolio_gif.gif?raw=true)

👉 [<b>TRY ME</b>](http://www.sandraspighel.com/) 👈

# Table of Contents

- [Short Description](#short-description)
- [Background](#background)
- [Technology Used](#technology-used)
- [Install](#install)
- [Project Development](#project-development)
  - [Initial Idea](#initial-idea)
  - [Set Up](#set-up)
  - [Basic SCSS](#basic-scss)
  - [Initial Idea](#initial-idea)
  - [Icons](#icons)
  - [Font](#font)
  - [Smooth Scroll & Scroll Snap](#smooth-scroll-&-scroll-snap)
  - [Menu](#menu)
  - [Projects](#projects)
  - [Contact](#Contact)
  - [Media Queries](#media-queries)
- [Final Thoughts & Project Wrap](#final-thoughts-and-project-wrap)
  - [Wins](#wins)
  - [Challenges / Bugs](#challenges-/-bugs)
  - [Key Learnings](#key-learnings)
  - [Possible Future Features](#possible-future-features)
- [License](#license)

## Short Description

Portfolio website presenting my work.

## Background

This is V2 of my portfolio as I had to implement a few changes due to the fact that the scroll behavior was not supported on all browsers, which made navigation difficult for some users. I took this opportunity to further implement flexbox to control layout and spacing within my sections.

## Technology Used

Built using Vanilla Vanilla [JavaScript](https://www.javascript.com/), [HTML](https://developer.mozilla.org/en-US/docs/Web/HTML) and [SASS](https://sass-lang.com/). Deployed with [GitHub Pages](https://pages.github.com/).

## Install

The website is mobile-friendly and accessible through the web browser.

### Installation Steps:

- Clone or download the repo
- Install dependencies: <code>yarn</code>
- Start server: <code>yarn start</code>

## Project Development

After working with frameworks during the Software Engineering Immersive Course for the past two months, I decided to go back to the basics and build my portfolio with vanilla JavaScript, HTML and SASS.

I hoped this would help me refresh my knowledge and also allow me to push myself out of my comfort zone a little bit by using event listeners again - which is what I struggled with most at the start of the course.

Style-wise, I wanted to challenge myself to implement more complex styling than I had the chance to do up to now, especially as I felt inspired by projects using transitions and animation. The portfolio was the perfect sandbox to do some exploring.

### Initial Idea

I started with researching other portfolio websites trying to find elements I liked or was intrigued by. I pulled a small list of elements that stood out, which stood at the basis of my portfolio built:

- Dark theme - I find it a lot easier to browse websites with a dark theme, so I wanted to implement this as my main theme, and then using colour accents for standout elements and links.
- I was fascinated by the smooth scroll within [this website](https://delassus.com/en/) and within [this website](https://melaniedaveid.com/) and decided to include smooth scroll and scroll snap into the main navigation of my portfolio: vertical scroll across my main sections, and horizontal scroll to view my projects.
- I liked how [this website](https://www.rezo-zero.com/) and [this website](https://adrienlaurent.fr/) used lots of space within its design to make it airy and asymmetric.
- Last, I liked the effect that oversized fonts bring, as seen in [this website](https://circle.sx/).

### Set Up

I started with setting up a new project and created my package.json, after which I installed node-sass.
I am storing my index.js into a dist folder, and created a folder called scss to host my scss files. In my package.json, I added a new script, so when I type the command ‘sass’, it is telling node-sass to watch the sass folder and output the compiled SASS to a css folder within the dist folder. Lastly, I linked my css within index.html and wrote a few lines of html to help with doing my basic styling as I go.

Before linking github, I added my node modules to a gitignore, because I do not want to add my dependencies to my git repository.

### Basic SCSS

For V1 of the portfolio, I started with giving my whole page a border-box to ensure any padding I add will remain within my box model, in other words the total size includes any borders and padding. I then set the body height to 100% and the margin to 0, and wrapped my whole main section in 4 rem of space around to push it a bit further from the edges. I did not want to have any scroll bars visible within my page so I also set the overflow to hidden within main. Last, I imported Montserrat and added this as my font-family. I will discuss my font choice a little bit further down.

In styling the body per my desired colour scheme, I set a primary colour variable in SASS as grey (#444) so I can build depth by lightning from this, and height by darkening. I then set the body to my primary colour and the font colour to #f5f5f5 as the #fff seemed a little too bright for the eyes. I also added a line-height of 1.5 to make reading a bit easier.

For V2, my basic set up included:

- Assigning a primary background color, then a primary font color, as well as primary and secondary font accent colours.
- Setting my font colour to change if the background is changing colour so we achieve a good contrast between font and background colour. This was inspired by Traversy's Responsive portfolio project [SASS set up](https://www.youtube.com/watch?v=HguAyYnWBuU&list=PLillGF-RfqbYoGoCjKoMOkVznV6aSXKzU&index=2)
- Trying to achieve better control over the font size across different browsers and devices by installing normalize.css, using the box model and setting the rem size to be equal with one pixel. This was inspired by research around sass mixins and ways to implement font sizes that would be relative to viewfinder height, in particular [this article](https://snook.ca/archives/html_and_css/font-size-with-rem) and [this article](https://coderwall.com/p/uck6gg/a-sass-mixin-for-dead-simple-rem-font-sizes)

Here is my starting SCSS for V2:

```
$primary-color: #444;
$font-primary-color: #f5f5f5;

// Set text colour
@function set-text-color($color) {
 @if (lightness($color) > 40) {
   @return $font-dark-primary-color;
 } @else {
   @return $font-primary-color;
 }
}

html {
 font-size: 62.5%; //This way, 1rem = 10px, making it easier to define my text-sizes through the document
}

// mixin making 1 rem
@mixin fontsize($size) {
 font-size: $size * 1px;
 font-size: $size * 0.1rem;
}

// * Overall Style
* {
 box-sizing: border-box;
 font-family: "Montserrat", sans-serif;
}

body {
 // Set main text colour
 background-color: $primary-color;
 color: set-text-color($primary-color);

 // Set font sizes
 font-size: 20px;
 text-align: right;

 h1,
 h2,
 h3,
 h4,
 h5 {
   font-weight: 800;
   margin: 0;
   line-height: 1.8;
 }

 h1 {
   font-size: 6rem;
 }

 h2 {
   font-size: 4.2rem;
 }

 h3 {
   font-size: 3rem;
 }

 h4 {
   font-size: 2.5rem;
 }

 h5 {
   font-size: 2rem;
 }

 p {
   font-weight: 400;
   font-size: 1.6rem;
   line-height: 1.5;
 }
```

### Icons

I decided to use FontAwesome and Devicon to generate my icons across the project.
Devicon allows free access to icons without having to register. For FontAwesome, you are required to create a user account before you can use icons, but the process is fast and you get free access to a great selection of icons. I used a hot chilli pepper for my open menu button (to stick to my overall theme), as well as the respective icons for my LinkedIn, GitHub and Twitter, and for each skill within the skills section.

### Font

After preliminary research, I decided to search for three kinds of fonts, all sans serif, and narrowed down to the following options:

1. Bold and sharp for titles and heavy quotes: Montserrat stood out as the best choice for oversized titles.

2. Regular weight for menu and other stand out text elements: I liked Questrial, Heebo and Montserrat.

3. Thin, clean and easy to read light text for the rest of the content. I wanted something resembling Helvetica, which would look good for chunks of text. The two fonts to stand out best were Josefin Sans and Montserrat.

As Montserrat looked best across the board, I selected this as my only font option.

## Smooth Scroll & Scroll Snap

As in version 1 of the portfolio I had a lot of issues with the sections overflowing onto the next section when the screen was resized (or not open with full viewport height), I decided to fully rely on flexbox in this version, so that all my content would be arranged better within my section areas, and it will allow me to better prevent overflows. To be able to see my areas better, I assigned colours to each section, as well as to all divs I worked with. I started with inserting my main HTML content, splitting into sections in preparation for the smooth scroll implementation.

```
 // Sections
 .outer-wrapper {
   width: 100vh;
   height: 100vw;
 }

 .wrapper {
   display: flex;
   flex-direction: column;
   height: 500vh;
   width: 100vw;
 }

 .slide {
   height: 100vh;
 }

 #home {
   background-color: pink;
 }

 #about {
   background-color: palevioletred;
 }

 #skills {
   background-color: plum;
 }

 #projects {
   background-color: purple;
 }

 #contact {
   background-color: magenta;
 }
```

Implementing the smooth scroll and scroll snap took me a while to get my head around, but I managed to get it going after reading about smooth scroll and watching [this video tutorial](https://www.youtube.com/watch?v=y9nlfqT4s9s).

I relied on a similar structure for both vertical and horizontal scroll: Wrapper / slides wrapper / slides. For example, my horizontal scroll:
HTML:

```
   <section id="projects" class="slide">
       <h1>projects</h1>
       <!-- Wrapper for the four projects -->
       <div class="projects-wrapper">

         <!-- Wrapper for horizontal slides -->
         <div class="h-slides-wrapper">

           <!-- Project 1 slide -->
           <div class="h-slide">Project 1</div>
           <div class="h-slide">Project 2</div>
           <div class="h-slide">Project 3</div>
           <div class="h-slide">Project 4</div>
         </div>
       </div>
       <!-- <h5>8 days, solo project</h5> -->
     </section>
```

SCSS:

```
#projects {
   background-color: purple;

   // Align title and projects area within the section area
   display: flex;
   flex-direction: column;

   // Implement horizontal scroll
   .projects-wrapper {
     background-color: teal;
     height: 80vw;

     overflow-y: scroll; // enable horizontal scroll
     scroll-behavior: smooth;
     scroll-snap-type: x mandatory;

     .h-slides-wrapper {
       display: flex;
       flex-direction: row;
       width: 400vw;

       .h-slide {
         // individual slide
         width: 100vw;
         height: 80vh;
         scroll-snap-align: center;
         background-color: red;
       }
     }
   }
 }
```

## Menu

For V1, I did a minimal HTML text for my nav bar: a small menu (Home, About, Projects, Contact, plus an X to close the menu) within a div with the id of side-menu. I also added a div with the class of open-side-menu and the favicon of a chilli pepper which would function as my menu open button - as this would be a burger menu.

I then added two events, openSideMenu on the chilli logo, and closeSideMenu on the X. The functions for these two are straight forward, adding width to the menu and pushing the rest of the page content to the right with the exact same number of pixels. I decided to use pixels to ensure I always have the same width for the menu, no matter the device used.

While working on the website, it became increasingly obvious that the close button was dispensable, and that a much smoother user experience would involve simply opening and closing the menu from the same button. I decided to crefactor my code by adding a showMenu variable to keep track of the menu position - open or closed - and to change the page accordingly.

```
    // Set initial state of menu
    let showMenu = false
    menuBtn.addEventListener('click', toggleMenu)

    function toggleMenu() {
      if (!showMenu) {
        document.getElementById('side-menu').style.width = '250px'
        document.getElementById('main').style.marginLeft = '250px'
        return showMenu = true
      }

      document.getElementById('side-menu').style.width = '0'
      document.getElementById('main').style.marginLeft = '0'
      return showMenu = false
    }
```

I styled the menu the same as V1, with the difference of implementing all my measurements in rem instead of px, so that I can maintain unit consistency throughout the project.

I started with styling my menu button, which I assigned a fixed position so it doesn’t change position when the window is scrolled. I also gave it a z-index of 2 to ensure it will remain on top of every other element on the page. The chilli button would change colour upon hover.

The menu would be placed at a z-index of 1, on a darker see-through background, and it would slide out smoothly from the left side.
The links would change colour and increase in size upon hover.

The main content of the website would also be pushed to the side, but at a slower pace than the menu so it can be seen moving smoothly from underneath the see-through menu. I quite like how the page rearranges itself gradually as the text moves to the right, so I might not apply any overflow to cut out any of the body width when the menu moves.

To keep my SCSS easy to read and work with, I decided to separate it into different files:
I moved all my variables into a newly made SCSS file called \_variables.scss, I then created a menu.scss to handle everything related to my menu.

## Projects

To avoid the main issue I had in V1 of the portfolio where people could not navigate from one project to another using the horizontal scroll due to browser compatibility, besides implementing the same process as the vertical scrolling, I also created numbered links to each project and included these at the bottom of the slide to offer an alternative to scroll navigation.

```
  <!-- Project Navigation Menu -->
         <div id="project-navigation-menu" >
           <a href="#project1" class="project-link">1</a>
           <a href="#project2" class="project-link">2</a>
           <a href="#project3" class="project-link">3</a>
           <a href="#project4" class="project-link">4</a>
         </div>
```

I then proceeded to add the project content and styling. I did not like how the project slides would get cropped in V1, and I wanted to avoid the many issues I have previously had with content overflowing from other sections.
I decided to use flexbox in arranging all content and to allocate an entire viewfinder width to each project. This behaves a lot better at screen resolution changes, and allows me more control over placing and spacing the content on the page. I used the viewfinder width to control how much the user sees from the projects, along with flexbox to keep everything spaced out evenly across the page:

```
#projects {
   // Align title and projects area within the section area
   display: flex;
   flex-direction: column;
   h1 {
     padding: 0 8rem 0 0;
   }

   // Set wider page padding to allow projects to take up full width
   padding: 0;

   // Implement horizontal scroll
   .projects-wrapper {
     overflow-y: scroll; // enable horizontal scroll
     scroll-behavior: smooth;
     scroll-snap-type: x mandatory;

     .h-slides-wrapper {
       display: flex;
       flex-direction: row;
       width: 400vw;

       .h-slide {
         // individual slide layout
         width: 100vw;
         height: 80vh;
         scroll-snap-align: center;
         display: flex;
         flex-direction: column;
         align-items: center;
         justify-content: space-evenly;

         // Remove scroll bar from projects and stops overlapping external content
         overflow: hidden;

         // Set project padding to line up with page padding
         padding: 2rem 8rem 0 6rem;

         text-align: justify;

         h5 {
           text-align: left;
         }

         a {
           color: $font-accent-color;
           &:hover {
             animation: blinkingTextAccentPrimaryAccent 2s infinite;
           }
         }

         span > a {
           color: $font-primary-color;
           &:hover {
             animation: blinkingTextAccentPrimaryAccent 1.2s infinite;
           }
         }

         .project-image {
           display: flex;
           flex-direction: column;
           align-items: center;
         }

         .project-text {
           width: 80%;
         }

         .tech-list {
           color: $font-secondary-accent-color;
         }
       }
     }
   }
```

And I added a navigation menu to help users navigate project pages if their browser is not compatible with scroll-behaviour, as this [might be an issue](https://caniuse.com/?search=scroll-behavior).

```
   // Align project navigation menu
   #project-navigation-menu {
     text-align: center;
     padding: 0 0 2rem 0;
     font-size: 3rem;
     font-weight: 800;

     .project-link {
       padding: 1.5rem 1rem 0 0;
     }
   }
 }
```

## Contact

I built the contact page using flexbox and styling with the same animation and transitions I used throughout the rest of the website. I used the flickering animation for the call to action with link, and the transitions to the social media icons linking to my profiles.

Last, the contact page was also built using flexbox. I was keen to have a lot of space within the website, and especially on the contact page, so that the information and links stand out easily.

## Media Queries

I was keen to ensure my site can be viewed on as many devices as possible, so I wrote 5 different media queries based on the device screen size:

```
// Media Query Mixins:
// Small Smartphone
@mixin media-Xsmall {
  @media screen and (max-width: 470px) {
    @content;
  }
}

// Smartphone
@mixin media-small {
  @media screen and (min-width: 471px) and (max-width: 555px) {
    @content;
  }
}

// Tablets & Small Laptops
@mixin media-medium {
  @media screen and (min-width: 556px) and (max-width: 768px) {
    @content;
  }
}

// Desktops & Laptops
@mixin media-large {
  @media screen and (min-width: 769px) and (max-width: 1170px) {
    @content;
  }
}

// Widescreens
@mixin media-Xlarge {
  @media screen and (min-width: 1171px) {
        @content;
  }
}
```

Due to having used flexbox throughout, the adjustments mainly had to do with font sizes and re-shaping the flexbox layout. Due to the height and width of very small screens, I decided not to display portfolio images for these devices, to ensure that all the written content is accessible. I have used different sized images for all other media queries.

# Final Thoughts & Project Wrap

I am overall happy with how the portfolio looks. There are small trims and changes I am thinking of, but the style and mood will remain similar.

## Wins

1. Feeling a lot more confident with event listeners, and working with the DOM again after learning React has also given me a stronger understanding of how the latter works.
2. I learned to use scroll behavior for both horizontal and vertical scroll, and scroll snap.
3. The overall look is what I had in mind, and I enjoyed pushing myself to try something different.

## Challenges

1. The horizontal scroll behavior has been challenging to begin with, and did not function correctly within V1 of the website. Re-doing the website and implementing the scroll behavior before doing any other styling has helped me understand its mechanics better. The solution (adding the numbers at the bottom so users can navigate to a project without scrolling) to the scroll issue also strengthens the overall user experience by offering a visual notification of the existance of other project slides.
2. In V1, I split the skills in categories trying to keep them separate. However, this made the page feel cluttered and crowded. Removing the categories and simply grouping all skills within a wrapped layout has helped this section look al lot tidier and neater.
3. Media queries were not easy to work with. What helped me progress was changing the background colour for each screen size and work my way through the website section by section adjusting as required. Choosing to use flexbox has cut down on a slot of the styling I had previously done in V1.

## Key Learnings

1. Horizontal and vertical scroll behavior, and scroll snap
2. More practice with media queries
3. Lots of practice with flexbox
4. More parctice with SASS

## Possible future features

1. A toggle to change the background colour
2. Implementing playful animations on the home page
3. Changing cursor when hovering over menu button
4. Hiding the horizontal scroll bar from the projects section

# License

MIT
