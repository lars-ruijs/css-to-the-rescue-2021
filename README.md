# CSS to the Rescue
In the course CSS to the Rescue, you will learn about and apply new techniques of CSS in a self-selected assignment. In this case the styling of a restaurant menu for which only an HTML structure was supplied. The look of the menu is completely up to you, as long as you learn to apply new CSS techniques. To make it more challenging, you have to consider two constraints and select at least one context.   

Below I have described my weekly progress:

## Week 1
In this first week, I have been thinking about how I want to approach the final assignment. First, I chose to style the restaurant menu. Next, I looked for inspiration online for beautiful menus and posters. In doing so, I came across a number of posters and menus with a 50s theme. I quickly thought of a typical American diner that always uses beautiful neon lighting at night. My challenge is to transform the experience of a classic diner into a semi modern interactive digital version. I promptly prepared a first draft after this:

<img alt="sketch for website" width="50%" src="https://user-images.githubusercontent.com/60745347/107031073-eabc1880-67b1-11eb-9646-25b7fcc603ad.JPG" />

### Restrictions 
As two restrictions, I chose:
- Using a maximum of two colors;
- Making the site responsive without using any media queries. 

I would still like to make my site colorful, without "violating" the two color rule. According to my teacher Vasilis, there are enough tricks in CSS to still get multiple colors while using only one color code. The second restriction was also something I had never done before. I knew how to make a grid responsive without media queries, but for other parts I always used media queries to tweak things. 

### Context
Originally I was thinking of choosing the context prefers-color scheme or a print stylesheet. Note that in week 3 I made a different choice. 

### First start
The first day we could start the final assignment, one of the things I started doing was selecting appropriate fonts. Then I started looking at how I could start adding a realistic neon styling to the text. Below I have put down a screenshot of one of my first attempts at styling the logo:

![1st version of neon logo](https://user-images.githubusercontent.com/60745347/109178752-7a3d6180-7789-11eb-9fdc-fcea0d732a90.png)

Next week I will continue to design the logo. 

## Week 2
In the first week, I created a first version of the logo. It was quite difficult to make a nice text shadow that looks like a neon light. I also used too many colors. At first I thought that it would be almost impossible to make a realistic shadow with only two colors. After a lot of trial and error, I found that a white text color and a light white "glow" around the text would work well to support the blue and light blue color. The text shadow is constructed by the offset/displacement of the x and y values. Then you define the degree of blur (i.e. how sharp the shadow is visible) and the color. 

```css
text-shadow: 0.1vw 0 0.25vw #fff; /* plus a lot more :) */
```

### The logo
To make the logo more in keeping with the theme of a 1950s dinner, I decided to put shapes around the logo. Sort of like [this](https://www.neon-light.net/proddetail.php?prod=nl-109502-the-50s-diner-circle-neon-sign) neon sign. I personally liked it better to have multiple repetitions of the shape running behind the text, like this sketch: 

<img alt="sketch of logo" width="50%" src="https://user-images.githubusercontent.com/60745347/109180676-6a268180-778b-11eb-8573-895578fd612c.JPG" />

To create this effect I added several empty div elements to the HTML. During the introductory assignments of this course, I learned about 3D space in CSS from some fellow students. With `translateZ` I can move the shapes on the Z axis, either closer or further away from the viewer. With the CSS property `perspective`, as the name suggests, you can adjust the perspective. The smaller the value, the deeper the shapes disappear into the "tunnel" so to speak. With `translate()` I can adjust the X and Y position so that the shapes fit together. In the end, it was quite difficult to get the shapes to fit together correctly. Finally, after many attempts to tweak the translate and perspective options this was the result: 

<img alt="neon logo with shapes" width="50%" src="https://user-images.githubusercontent.com/60745347/109180134-dce32d00-778a-11eb-9dd2-e3cec50ca9a3.png" />

### The colors
Even though I chose the two color "restriction" I still wanted to add more colors. For this I was able to use the CSS filter `hue-rotate`. This allows you to rotate the color spectrum and thus get a different color with the same color codes. To make the colors brighter I also used the `saturate` filter. 

### Adding animations
With neon, it of course fits that things flash and blink. That's why I wanted to add animations to the logo. I hadn't done much with animating in CSS before, so that seemed like a good point to learn more about. I ended up creating a keyframe animation where it looks like the light is flickering on and off quickly. I did this by removing the text shadow from time to time and making the text darker. Of course I was not allowed to use a different color for this, so I applied another CSS filter: `brightness`. 

```css
@keyframes electric {
  78% {
    filter: none;
    text-shadow: inherit;
  }
  79% {
    filter: brightness(0.2);
  }
  80% {
    text-shadow: none;
  }
  81% {
    filter: none;
    text-shadow: inherit;
  }
  /* ETC ... */
 ```

Another part of the logo that I was able to play with is the perspective. By making the perspective number lower at times and then higher again, you get a sort of zoom in/out effect.

```css
@keyframes perspective {
  0% {
    perspective: 10px;
  }
  50% {
    perspective: 18px;
  }
  100% {
    perspective: 10px;
  }
}
```

I also created a keyframe animation for the tagline "Best food in town," which makes it look like that part of the sign keeps turning on and off. 

To give a sense of randomness, I gave the different elements different animation durations or an animation delay. This makes it seem as if the letters and shapes go on and off randomly.  

```css
header section div:nth-child(5) {
  animation-delay: 0.5s;
}
```

### The menu
Since I actually liked the logo quite a bit, I thought it would be a waste to put the logo small in the upper left corner. I had originally sketched this that way, but it makes the logo a lot less eye catching. From there, I came up with the idea of then making the logo look like a Drive-Thru sign - by putting it on a pole. On this pole I could then display the menu. Below is a screenshot of what I had created at the end of week 2: 

<img alt="neon logo on a pole" width="50%" src="https://user-images.githubusercontent.com/60745347/109190080-04d78e00-7795-11eb-9945-42275a6ac24a.png" />

## Week 3
Last week I had the idea of putting the menu on the pole of the drive trough sign. After feedback, it became clear to me too that the Internet doesn't need a pole, so it was good to come up with a new idea. This I found quite difficult. I then made some sketches and a start of two sketches with CSS. Fortunately, I had scheduled the "Loose with the CSS hips" session, to get additional feedback and ideas for my concept. Here my teacher Vasilis advised me to continue with the first idea and elaborate it with interaction. I could have the menu items expand when someone clicks on a shape. 

<img alt="sketch of menu" width="50%" src="https://user-images.githubusercontent.com/60745347/109191996-086c1480-7797-11eb-95db-eb3de5dda864.JPG" /> 
<img alt="sketch of menu in css" width="50%" src="https://user-images.githubusercontent.com/60745347/109192057-16ba3080-7797-11eb-861b-dca9f3c26c75.png" />

### Adding interaction
Previously, I had participated in a session on using interaction with CSS. Here I learned that you don't necessarily need JavaScript to make elements interactive. It seemed like a good point to learn more about by applying it myself. With making the menu interactive, I used checkboxes and labels. The checkboxes are separate outside the `<main>` element. The` <header>` elements are now placed within a `<label>`, so that by clicking on a label you check the corresponding checkbox. Because the checkboxes are outside the `<main>` element, you can use the sibling selector `~` to make the `<main>` and the elements within it respond to interaction. 

**The checkboxes**
```html
<input type="checkbox" name="food" id="noshes">
<input type="checkbox" name="food" id="boards">
<!-- And many more -->
```

**The labels**

The label-tags are placed around the header of each section. 

```html
<section>
 <label for="noshes">
   <header>
     <h2>Noshes</h2>
     <p>for tiny tummys</p>
   </header>
  </label>
  <!-- More elements -->
</section>
```

**Making the interaction work**

To select the first section when the first label is clicked, I used the following selector:
```css
input[type="checkbox"]:first-of-type:checked ~ main section:first-of-type {
  flex-grow: 1;
  height: 100%;
}
```
Here, the clicked section indicates that it may take up all available space. 

### Removing the elements
When a label is clicked it means that the other menu items should no longer be shown. At first I used `display: none`. The disadvantage of this is that you cannot animate this change. This made the opening and closing of menu items look very strange. After searching for other possibilities, I came up with the following:  

```css
input[type="checkbox"]:first-of-type:checked ~ main section:not(main section:first-of-type) {
  position: absolute;
  top: 0;
  width: 0;
  height: 0;
  font-size: 0;
  opacity: 0;
  transform: scale(-1);
}
```

By setting all the values for size, and thus visibility, to 0, I could still hide the elements. The only disadvantage of this was that the disappearance of the elements towards the top was also animated. To prevent this I added a negative animation delay. This causes the animation to start earlier and in this case it is not visible. 

```css
  transition-delay: -2s;
```


### Result of Week 3
To better match the labels with the colorful logo, I also applied CSS filters to the labels. I captured the end result of what the interaction looks like as a gif: 

![interaction with menu items](https://user-images.githubusercontent.com/60745347/109490189-2df36980-7a88-11eb-83ed-3c2ebfbfda7a.gif)


### Change in context 
After the feedback at the end of week 3, I decided to change my context. Initially, I thought about designing "prefers-color-scheme" or "print" for the context. Because my site is rather heavy on your computer, my teacher Vasilis came up with the suggestion to look at available media queries for something like low-end devices or people who want to use less battery. 


## Week 4
This week I focused on taking context into account. Last week I received feedback from Vasilis that it might be a good idea to take into account devices that have lower graphics performance or users who want to save their battery. I then started looking for suitable media queries. 

### Prefers-reduced-motion
The media query prefers-reduced-motion allows users to indicate that they prefer not to see (busy) moving elements on the website. For example because they get nauseous or want to save battery. Of course, my website is full of animations and transitions, so it should be possible to disable these in a good way. For this I first saved all the animation properties as a custom variable.

```css
  --animation-electric: electric ease-out infinite;
  --animation-blinking: blinking linear infinite 1s;
  --animation-perspective: perspective ease-in-out infinite 5s;

  --menu-transition: all ease-in-out 1s;
```

Because these settings are now stored as custom variables, I can modify them more easily. Below you can see how I applied the media query. 
```css
@media (prefers-reduced-motion: reduce) {
  /* Remove animations > make transitions slower */
  :root {
    --animation-electric: none;
    --animation-blinking: none;
    --animation-perspective: none;

    --menu-transition: transform 3s ease-in-out;
  }
}
```

I remove the animations and make sure the transition has a longer duration, so the animation looks a little more subtle. In addition, I adjusted some hover changes so that they also look less "intense". For the flying in and disappearing of the various menu headers, I removed the transition, because it moved rather intensely. Below you can see how the interaction with the menu elements occurs when prefers-reduced-motion is enabled. Elements still respond to hover, but a lot more subtly. Opening and closing a menu element now happens instantly, without an intense animation.

![opening and closing menu items](https://user-images.githubusercontent.com/60745347/109668202-37a4cc00-7b71-11eb-9fba-0c1ad108a848.gif)

### Prefers-reduced-data
In  addition to creating a version without animations, I also wanted to create a sort of "lite" version of my website. Here I thought of a piece from guest speaker Vitaly's presentation, where he shortly talked about a completely new CSS media query called: prefers-reduced-data. According to [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-data), the idea behind this media query (for now) is to consume less internet traffic. For example, because you are in an area with slow internet, because you want to save your phone's battery or have a lower-end device. So in my case it can also be used well for delivering a less intensive website. My goal here is to maintain or modify some of the functions of the website so that they are less intensive on the browser and use less data. It is important to note that this media query is currently not supported by any browser. It is still in the "editors draft" phase. In Chrome you can simulate this feature after enabling Experimental Web Features.  

<br>

**Local fonts**

One of the things I did first was to switch to locally installed fonts. CSS only imports external fonts if they are addressed by a property. By switching from external fonts to locally available fonts, the browser does not need to download external fonts. Below you can see how I applied this: 

```css
@media (prefers-reduced-data: reduce) {
  :root {
    /* Only use local fonts */
    --main-heading: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
      Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
    --sub-heading: "Brush Script MT", cursive;
    --body-text: "Bradley Hand ITC", cursive;
}
```
Actually, even better would be to call the `@import` and `@font-face` only when prefers-reduced-data is equal to `no-preference`. But since there is currently no browser support for this media query, it is currently not wise to implement if you want to display your own fonts on your site.

<br>

**Creating a "lite" version**

In addition to reducing the fetching of external fonts, I also wanted to optimize the site in terms of load time and make it suitable for devices with less computing power. One of the tools I used for this is [CSStriggers](https://csstriggers.com). Here you can see for many CSS properties how they affect rendering by the browser. Does it affect the layout, composition and does the browser need to repaint? Through the site I found out that changing text-shadow and box-shadow by using animations affects all three browser operations. So this is very intensive for the computer to perform. 

![css triggers](https://user-images.githubusercontent.com/60745347/109674587-5312d580-7b77-11eb-85f9-084260148dc6.png)


I then set out to find a good combination of animation while using as little computer power as possible.  Because the use of text-shadow and box-shadow are very intensive to animate, I had to omit these effects from the animated elements. In order to still achieve a neon effect I decided to give the title and subtitle a text-shadow, but to leave out the animation. On the background of the logo I still use an animation, but without the neon shadow, so that less computer power is used. The original keyframe animation I used with the logo included text shadows. Even though this one did not apply a new shadow, the performance turned out to be better when I left it out completely. For this I created a "lite" keyframe animation:

```css
@keyframes electricLite {
  78% {
    filter: none;
  }
  79% {
    filter: brightness(0.2);
  }
  /* ETC */
```

This is how the logo and its animation look like when prefers-reduced-data is enabled:

![logo lite mode](https://user-images.githubusercontent.com/60745347/109803854-d8eb5b00-7c21-11eb-96e4-9d6d5a0620f1.gif)

In addition to the logo, all menu elements had a text-shadow and a box-shadow. These elements have a hover transition and a transition when they flip open and out. Again, the neon shadows made these animations less smooth. Here I changed the text color to light blue and gave the elements a light blue border color. Then I applied the CSS filters to still get "bright" colors that look a bit like neon. This gave the following result: 

![menu options in lite mode](https://user-images.githubusercontent.com/60745347/109808708-bd834e80-7c27-11eb-962c-4d5ec5ca9594.gif)

<br>

**Performance test**

To check whether the "lite" version of the website is actually less intense for your computer, I ran a performance test via Chrome. Below you can see the results of it. The results on the left are from the "normal" website and on the right the "lite" version. As you can see, this version is less intense for your computer. The browser takes less time to render and the browser's "painting" process has dropped significantly: from 65ms to 2ms. Google Chrome's GPU process decreased by about 20%. When you use the site you also notice that it works a lot smoother. 

<img alt="performance test" width="60%" src="https://user-images.githubusercontent.com/60745347/109810232-90d03680-7c29-11eb-8454-d580fd44bb53.png" /> 

### Adding keyboard support
To ensure that users who want to control the website with a keyboard can actually do so, I made some changes to my CSS code. Initially, I had hidden the checkboxes (which control interaction) by using `display: none`. Unfortunately, it turned out that all the interaction options could then no longer be used. I therefore had to hide the checkboxes in a different way, by using `width = 0` and `opacity = 0`. Then I was able to have the menu labels respond to the focus state of the checkboxes. To make sure that the focus state is only visible when using keyboard navigation I used `focus-visible`. This way it is as clear as possible that this is the active selection. 

```css
input[type="checkbox"]:first-of-type:focus-visible ~ main section:first-of-type {
  margin: 0 3em;
  transform: translateY(-3em) scale(1.3);
  filter: hue-rotate(160deg) saturate(2) brightness(110%);
}
```

The focus state becomes active when you move through the elements with tab. A menu section can be opened by pressing the space bar. The effect looks like this:

![focus state menu items](https://user-images.githubusercontent.com/60745347/109814428-c9264380-7c2e-11eb-99dd-b549c561cc5c.gif)
