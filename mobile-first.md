# Mobile First Web Design

## Mobile First started as a book

![Luke Wroblewski](./img/12-lukewroblewski_photo022012.jpg)

In 2011, Luke Wroblewski wrote a book called "Mobile First" that made the case for making web design for mobile devices come first in the design process. It was the start of a revolution in digital design whose impact is still felt today.

[https://www.lukew.com/resources/mobile_first.asp](https://www.lukew.com/resources/mobile_first.asp)


## How to Design a Web Site using Mobile First CSS 

### Anatomy of a CSS Style Sheet

|  CSS  |  Purpose  |
| ----------------- | ------------------ |
| @import | Place font import rules first. Placing them further down the sheet may prevent them from working at all.  |
| CSS Reset | If you are not linking to a separate CSS reset file in the HTML \<head>, add CSS reset code here. Examples can be found in this [GWD Repo](https://github.com/JACGWD/CSS-Reset-Selector). |
| Default Rules (mobile first) | CSS style rules that will appear at any screen size: fonts, colors, margins, padding. These should be designed for the smallest viewport you want to support. |
| First media query | This set of CSS **tweaks** the mobile first CSS page layout rules for a slightly larger viewport. For example a bigger smartphone or small tablet. |
| Second media query | This second set of CSS tweaks **the combination of the default rules plus the first media query page layout rules** for an even slightly larger viewport. For example a bigger tablet or smaller desktop/laptop screen. |
| Continue repeating with more media queries as necessary | The more complex the design, the more media query tweaks you will need to write. |


#### Mobile First CSS is based on using 'Minimum Width' media queries

At its simplest, web design is all about designing small and working your way up to larger screens. 

Most of the work is at the top (beginning) of the stylesheet: for the smartphone (default styles) and for the first transition to landscape orientation (because smartphones are usually held in portrait mode). After that, you normally see the number of CSS rules decline quickly as only small tweaks are needed in between different size screens that use the same layout.

1. Default styles (smartphone styles that apply to all sizes)
2. Minimum width media query 1: Tweak the design for larger viewports like tablets
3. Minimum width media query 2: Tweak the design for larger viewports like small laptop screens
4. Minimum width media query 3: Tweak the design for larger viewports like larger laptop screens
5. Minimum width media query 4: Tweak the design for larger viewports like desktop screens
6. Minimum width media query 5: Tweak the design for larger viewports like projectors

### Media Queries are also known as 'Break Points' 

![content breakpoint](./img/13-breakpoint.png)

As a designers, your first job is to design a web site for use on mobile phones. Basically one long column. The design looks good on a very tall skinny artboard.

However, if the user has an iPad, the proportion of the artboard changes. It is less rectangular and more square. The design that looked good on mobile breaks. Literally. So, at a certain viewport size the design becomes broken and needs to be fixed. That is the "breakpoint". At whatever size that is, you create a media query rule that applies to that viewport size and bigger. In that media query you tweak your rules so the design looks good again.

Mobile First design is about doing just that, over and over again, until you reach the maximum desktop size you want to support.

<blockquote>

#### Tip

Pro designers use web site visitor statistics to find out at what viewports sizes their designs are commonly seen in the real world. If 1% of your users use an oddball viewport size, it might not be worthwhile to spend the time and effort (and money) to support that size. The design may not be perfect at that size, but the user will still receive the information provided by that page.

</blockquote>

### What are media queries for?

The point of a media query is to:

- Query ("ask") the browser to find out **what size the viewport is**. 
  - (Media queries can find out many other browser capabilities, but screen size is the most basic.)


- Apply design rules in this order:
    - Rules that apply to all sizes; aka the "default styles".
    - Rules from other (usually smaller) viewport sizes that can be inherited by the current one. 
    - Rules specific to the current size.

#### In CSS the Last Rule Wins

If your CSS has rules that conflict, the one written last (read last by the browser) wins.


    Line 10:   body { background-color: white; }
    Line 20:   body { background-color: purple; }


In this case, the background color will be purple.


#### Examples

##### Default Styles 
If you define the background color as being white in the **default rules (before/above any media queries in the stylesheet)**, the web page will always appear white no matter what size the viewport. (Unless you override that elsewhere in the stylesheet, as seen above.)


    body { background-color: white; }


##### Adjust styles bigger than a certain size

If you use this media query below the default one:

    @media screen and (min-width: 1000px) {
        body { background-color: blue; }
    }


Any smartphone or tablet smaller than 1000px wide will have a white background color because:

1. The default rule (white background) is inherited.
2. The media query says that the viewport must have a **minimum viewport width of 1000px** for the blue background color rule to apply.

See: [W3Schools page on CSS 3 Media Queries](https://www.w3schools.com/Css/css3_mediaqueries_ex.asp)

