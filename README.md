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
In the first week, I created a first version of the logo. It was quite difficult to make a nice text shadow that looks like a neon light. I also used too many colors. At first I thought that it would be almost impossible to make a realistic shadow with only two colors. After a lot of trial and error, I found that a white text color and a light white "glow" around the text would work well to support the blue and light blue color. 

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

|<img alt="sketch of menu" width="30%" src="https://user-images.githubusercontent.com/60745347/109191996-086c1480-7797-11eb-95db-eb3de5dda864.JPG" /> | <img alt="sketch of menu in css" width="250%" src="https://user-images.githubusercontent.com/60745347/109192057-16ba3080-7797-11eb-861b-dca9f3c26c75.png" /> |
|--|--|
| A few menu ideas | Two selected menu ideas with CSS |

### Adding interaction
Previously, I had participated in a session on using interaction with CSS. With making the menu interactive, I used checkboxes and labels. The checkboxes are separate outside the `<main>` element. The` <header>` elements are now placed within a `<label>`, so that by clicking on a label you check the corresponding checkbox. Because the checkboxes are outside the `<main>` element, you can use the sibling selector `~` to make the `<main>` and the elements within it respond to interaction. 
