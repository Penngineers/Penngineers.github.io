---
layout: default
---

A warm welcome to all the people visiting our page. We are the team Penngineers. We are first year graduate students in the Electrical Engineering program at University of Pennsylvania specializing in Circuits and Computer Engineering. We designed the following game as a final project for our course ESE 5190: Embedded Systems. We had a lot of fun while building this project. We will be walking you through a detailed description of our project which will help you understand it in depth in case you wish to recreate it. 


# Overview of Project

We designed an arcade game called Whack-It-First inspired by the famous game Whack-A-Mole. However, instead of replicating the good old Whack-A-Mole game completely we decided to change it up in order to make it even more exciting to play. Our game, Whack-It-First is a two player game where two people need to team up to play this game together. The gaming interface consists of 4 arcade buttons in colors: Blue, Red, White and Yellow on each side which represent the moles, two green colored arcade buttons which indicate the commencement of the game, a speaker module which plays music at the same time as the green colored arcade buttons glow to indicate the commencement of the game, a pink colored arcade button which is required to be pressed to commence the game, a TFT display which guides the players by displaying instructions and a LED matrix which displays the score. Our gaming interface is as seen in the image below. Once the game commences, two same colored arcade buttons will glow on each side and the two players need to hit the glowing buttons in unison to record a score. In case, if the players do not hit the glowing arcade buttons at the same time or if one of the players hits the wrong arcade button or if the players exceed the wait time provided to hit the glowing arcade buttons, the game ends. As the game proceeds and the players cross a certain score which we have set as a threshold value, the game becomes faster and even more thrilling to play. We have linked a video capturing the game in action below. 

![11](https://user-images.githubusercontent.com/114092860/210121471-d875ff38-65bb-4c49-8b87-ba05d47df5e5.jpg)




[Link to another page](./another-page.html).

# Project Instructions

We decided to build a complete product and hence our project involved 3 stages: Product Design, Hardware Design and Software Design. We will be first walking you through Product Design.

# Product Design

We designed a box whose top surface would act as a gaming interface and the box would enclose all the circuitry thus making it look like a finished product. In order to do this, we first made a rough sketch on paper of how we would want our gaming interface to look like. As we planned to fit the arcade buttons, LED matrix and TFT display on the top surface of the box we measured all these components in order to create accurate slots on the top surface of the box where these components would be fitted. We looked up images showing the mechanical structure of the arcade buttons as shown below. Considering the width indicated in the images and leaving a 0.5 mm margin for error we decided on a diameter of 28.5 mm for the illuminating arcade buttons in colors: Blue, Green, Red, White and Yellow and a diameter of 30 mm for the non-illuminating arcade button in pink color. We measured the width and height of the LED matrix and TFT display using vernier caliper and made slots measuring 128mmx31mm and 56mmx35mm for the LED matrix and TFT display respectively. We then designed a box measuring 440mmx280mm with finger edge joints using MakerCase. We then downloaded the .dxf file from MakerCase and imported it to Adobe Illustrator in order to make the slots on the top surface of the box for the components. We then downloaded the .ai file and sent it for laser cutting. The box was laser cut using ¼  inch black acrylic. We have inserted the images of the files below and have also attached the files in the appendix.

## Mechanical Structure of Illuminating Arcade Button 

![Illuminating Arcade Button Mechanical Structure](https://user-images.githubusercontent.com/114092860/210121912-c7cb3af6-29b8-4bb5-a5f0-922c82c91fdf.png)

## Mechanical Structure of Non-Illuminating Arcade Button 

![Non-illuminating Arcade Button Mechanical Structure](https://user-images.githubusercontent.com/114092860/210121938-9d279b71-61a6-45c5-ae46-c15349c445d1.png)

## Image of .dxf File of Box

![dfx](https://user-images.githubusercontent.com/114092860/210122126-6352b6e4-f169-49ee-9118-489e80488696.png)


## Image of .ai File for Laser Cutting

![ai](https://user-images.githubusercontent.com/114092860/210122132-9314e15c-f433-4184-998d-38c5e59e3cbd.png)

# Hardware Design

We will first walk you through the components we used for building our project. Individual images of all components are shown below.

# Component List

![Components](https://user-images.githubusercontent.com/114092860/210121824-05cc6ce2-3017-44eb-a340-9cdf4974072c.png)

# Hardware Description 

We will now walk you through a detailed description of our hardware design. We used RP2040 PICO microcontroller which is based on Dual ARM Cortex-M0+ architecture. Though this game has many versions available online, ours is the first one to use RP2040 PICO microcontroller. The block diagram of our project is as shown below. As seen in the block diagram, the RP2040 PICO microcontroller is programmed to control the components such as the LED Matrix, TFT Display, Speaker Module, I2C breakout boards and the arcade buttons. Among all the versions of this project available online, ours is the only project to utilize I2C breakout boards as an alternative for replacing multiple I2C connections. Since a single I2C breakout board is responsible for 4 arcade buttons, we had to use 3 I2C breakout boards for controlling our 11 arcade buttons. Each I2C breakout board has a predefined I2C address which is 0x3A. Hence, we had to cut the PCB trace of the other 2 I2C breakout boards in order to assign them the I2C addresses 0x3B and 0x3C respectively. Thus, all 3 I2C breakout boards were assigned different I2C addresses which eliminated the problem of pin definition. The I2C breakout board 1 was assigned the I2C address 0x3B by cutting the A0 trace and is responsible for controlling the illuminating arcade buttons in colors: Blue, Red, White and Yellow on the right side of the gaming interface. The I2C breakout board 2 was assigned the predefined I2C address 0x3A as no trace was cut and is responsible for controlling the illuminating arcade buttons in colors: Blue, Red, White and Yellow on the left side of the gaming interface. The I2C breakout board 3 was assigned the I2C address 0x3C by cutting the A1 trace and is responsible for controlling the illuminating green colored arcade buttons and the non-illuminating pink colored arcade button. All the 3 I2C breakout boards have been chained together using the Stemma QT cable and thus connected to RP2040 PICO microcontroller. The RP2040 PICO microcontroller was mounted on the port expander so as to gain access to more GPIO pins and to also provide 5V power supply to the entire gaming interface as that was mainly the power requirement of the arcade buttons. The connections between the other components and RP2040 PICO microcontroller have been tabulated as shown below.

# Connection between the I2C Breakout Board and RP2040 PICO Microcontroller

![I2C Breakout Board Connections](https://user-images.githubusercontent.com/114092860/210122226-067df609-b259-486f-b3d5-66767ca2f8cf.png)

# Connection between Led Matrix and RP2040 PICO Microcontroller 

![LED Matrix Connections](https://user-images.githubusercontent.com/114092860/210122303-fc842193-8a89-4f00-bee3-336a6281a3d3.png)


# Connection between TFT Display and RP2040 Microcontroller 

![TFT Display Connections](https://user-images.githubusercontent.com/114092860/210122487-8bf67dec-22e7-45dd-9a77-ca3982eb664e.png)

# Connection between Speaker Module and RP2040 Microcontroller 

![Speaker Module Connections](https://user-images.githubusercontent.com/114092860/210122504-2e83328a-1c94-47d9-8053-80e8e0a6a0dd.png)


# Software Design

We will be walking you through our software design process now. We used Arduino IDE for programming our RP2040 PICO microcontroller. We downloaded the required libraries and have attached them in the appendix below. We used multicore functionality to run 2 individual tasks simultaneously. The first task was to register the button presses of the 2 players and record a score and the second task was to run the counter for the game. This allowed us to achieve our goal of building a perfect gaming experience with no delay. However, this was a difficult process as we had to integrate 3 I2C breakout boards which had 3 different I2C addresses assigned to them and were controlling 11 arcade buttons. The “void setup()” and the “void loop()” perform the first task as explained above while “void setup1()” and “void loop1()” perform the second task as explained above. The complete code has been attached in the appendix below.

[Link to another page](./another-page.html).



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
