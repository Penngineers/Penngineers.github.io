---
layout: default
---

A warm welcome to all the people visiting our page. We are the team Penngineers. We are first year graduate students in the Electrical Engineering program at University of Pennsylvania specializing in Circuits and Computer Engineering. We designed the following game as a final project for our course ESE 5190: Embedded Systems. We had a lot of fun while building this project. We will be walking you through a detailed description of our project which will help you understand it in depth in case you wish to recreate it. 


# Overview of Project

We designed an arcade game called Whack-It-First inspired by the famous game Whack-A-Mole. However, instead of replicating the good old Whack-A-Mole game completely we decided to change it up in order to make it even more exciting to play. Our game, Whack-It-First is a two player game where two people need to team up to play this game together. The gaming interface consists of 4 arcade buttons in colors: Blue, Red, White and Yellow on each side which represent the moles, two green colored arcade buttons which indicate the commencement of the game, a speaker module which plays music at the same time as the green colored arcade buttons glow to indicate the commencement of the game, a pink colored arcade button which is required to be pressed to commence the game, a TFT display which guides the players by displaying instructions and a LED matrix which displays the score. Our gaming interface is as seen in the image below. Once the game commences, two same colored arcade buttons will glow on each side and the two players need to hit the glowing buttons in unison to record a score. In case, if the players do not hit the glowing arcade buttons at the same time or if one of the players hits the wrong arcade button or if the players exceed the wait time provided to hit the glowing arcade buttons, the game ends. As the game proceeds and the players cross a certain score which we have set as a threshold value, the game becomes faster and even more thrilling to play. We have inserted a video capturing the game in action below. 

![11](https://user-images.githubusercontent.com/114092860/210121471-d875ff38-65bb-4c49-8b87-ba05d47df5e5.jpg)



https://user-images.githubusercontent.com/114092860/210121604-a76c3f98-8de4-450c-83e7-09b77e6d3ff3.mp4


[Link to another page](./another-page.html).

# Project Instructions

We decided to build a complete product and hence our project involved 3 stages: Product Design, Hardware Design and Software Design. We will be first walking you through Product Design.

# Product Design

We designed a box whose top surface would act as a gaming interface and the box would enclose all the circuitry thus making it look like a finished product. In order to do this, we first made a rough sketch on paper of how we would want our gaming interface to look like. As we planned to fit the arcade buttons, LED matrix and TFT display on the top surface of the box we measured all these components in order to create accurate slots on the top surface of the box where these components would be fitted. We looked up images showing the mechanical structure of the arcade buttons as shown below. Considering the width indicated in the images and leaving a 0.5 mm margin for error we decided on a diameter of 28.5 mm for the illuminating arcade buttons in colors: Blue, Green, Red, White and Yellow and a diameter of 30 mm for the non-illuminating arcade button in pink color. We measured the width and height of the LED matrix and TFT display using vernier caliper and made slots measuring 128mmx31mm and 56mmx35mm for the LED matrix and TFT display respectively. We then designed a box measuring 440mmx280mm with finger edge joints using MakerCase. We then downloaded the .dxf file from MakerCase and imported it to Adobe Illustrator in order to make the slots on the top surface of the box for the components. We then downloaded the .ai file and sent it for laser cutting. The box was laser cut using ¼  inch black acrylic. We have inserted the images of the files below and have also attached the files in the appendix.


# Hardware Design

We will first walk you through the components we used for building our project. Individual images of all components are shown below.

# Component List:




## Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)




### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
