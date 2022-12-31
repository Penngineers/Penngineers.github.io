---
layout: default
---

A warm welcome to all the people visiting our page. We are the team Penngineers. We are first year graduate students in the Electrical Engineering program at University of Pennsylvania specializing in Circuits and Computer Engineering. We designed the following game as a final project for our course ESE 5190: Embedded Systems. We had a lot of fun while building this project. We will be walking you through a detailed description of our project which will help you understand it in depth in case you wish to recreate it. 


# Overview of Project

We designed an arcade game called Whack-It-First inspired by the famous game Whack-A-Mole. However, instead of replicating the good old Whack-A-Mole game completely we decided to change it up in order to make it even more exciting to play. Our game, Whack-It-First is a two player game where two people need to team up to play this game together. The gaming interface consists of 4 arcade buttons in colors: Blue, Red, White and Yellow on each side which represent the moles, two green colored arcade buttons which indicate the commencement of the game, a speaker module which plays music at the same time as the green colored arcade buttons glow to indicate the commencement of the game, a pink colored arcade button which is required to be pressed to commence the game, a TFT display which guides the players by displaying instructions and a LED matrix which displays the score. Our gaming interface is as seen in the image below. Once the game commences, two same colored arcade buttons will glow on each side and the two players need to hit the glowing buttons in unison to record a score. In case, if the players do not hit the glowing arcade buttons at the same time or if one of the players hits the wrong arcade button or if the players exceed the wait time provided to hit the glowing arcade buttons, the game ends. As the game proceeds and the players cross a certain score which we have set as a threshold value, the game becomes faster and even more thrilling to play. We have linked a video capturing the game in action below. 

![11](https://user-images.githubusercontent.com/114092860/210121471-d875ff38-65bb-4c49-8b87-ba05d47df5e5.jpg)

https://github.com/JuiUpenn11/ESE-5190-Final-Project-Midpoint. 


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

## Component List

![Components](https://user-images.githubusercontent.com/114092860/210121824-05cc6ce2-3017-44eb-a340-9cdf4974072c.png)

# Hardware Description 

We will now walk you through a detailed description of our hardware design. We used RP2040 PICO microcontroller which is based on Dual ARM Cortex-M0+ architecture. Though this game has many versions available online, ours is the first one to use RP2040 PICO microcontroller. The block diagram of our project is as shown below. As seen in the block diagram, the RP2040 PICO microcontroller is programmed to control the components such as the LED Matrix, TFT Display, Speaker Module, I2C breakout boards and the arcade buttons. Among all the versions of this project available online, ours is the only project to utilize I2C breakout boards as an alternative for replacing multiple I2C connections. Since a single I2C breakout board is responsible for 4 arcade buttons, we had to use 3 I2C breakout boards for controlling our 11 arcade buttons. Each I2C breakout board has a predefined I2C address which is 0x3A. Hence, we had to cut the PCB trace of the other 2 I2C breakout boards in order to assign them the I2C addresses 0x3B and 0x3C respectively. Thus, all 3 I2C breakout boards were assigned different I2C addresses which eliminated the problem of pin definition. The I2C breakout board 1 was assigned the I2C address 0x3B by cutting the A0 trace and is responsible for controlling the illuminating arcade buttons in colors: Blue, Red, White and Yellow on the right side of the gaming interface. The I2C breakout board 2 was assigned the predefined I2C address 0x3A as no trace was cut and is responsible for controlling the illuminating arcade buttons in colors: Blue, Red, White and Yellow on the left side of the gaming interface. The I2C breakout board 3 was assigned the I2C address 0x3C by cutting the A1 trace and is responsible for controlling the illuminating green colored arcade buttons and the non-illuminating pink colored arcade button. All the 3 I2C breakout boards have been chained together using the Stemma QT cable and thus connected to RP2040 PICO microcontroller. The RP2040 PICO microcontroller was mounted on the port expander so as to gain access to more GPIO pins and to also provide 5V power supply to the entire gaming interface as that was mainly the power requirement of the arcade buttons. The connections between the other components and RP2040 PICO microcontroller have been tabulated as shown below.

## Connection between the I2C Breakout Board and RP2040 PICO Microcontroller

![I2C Breakout Board Connections](https://user-images.githubusercontent.com/114092860/210122226-067df609-b259-486f-b3d5-66767ca2f8cf.png)

## Connection between Led Matrix and RP2040 PICO Microcontroller 

![LED Matrix Connections](https://user-images.githubusercontent.com/114092860/210122303-fc842193-8a89-4f00-bee3-336a6281a3d3.png)


## Connection between TFT Display and RP2040 Microcontroller 

![TFT Display Connections](https://user-images.githubusercontent.com/114092860/210122487-8bf67dec-22e7-45dd-9a77-ca3982eb664e.png)

## Connection between Speaker Module and RP2040 Microcontroller 

![Speaker Module Connections](https://user-images.githubusercontent.com/114092860/210122504-2e83328a-1c94-47d9-8053-80e8e0a6a0dd.png)


# Software Design

We will be walking you through our software design process now. We used Arduino IDE for programming our RP2040 PICO microcontroller. We downloaded the required libraries and have attached them in the appendix below. We used multicore functionality to run 2 individual tasks simultaneously. The first task was to register the button presses of the 2 players and record a score and the second task was to run the counter for the game. This allowed us to achieve our goal of building a perfect gaming experience with no delay. However, this was a difficult process as we had to integrate 3 I2C breakout boards which had 3 different I2C addresses assigned to them and were controlling 11 arcade buttons. The “void setup()” and the “void loop()” perform the first task as explained above while “void setup1()” and “void loop1()” perform the second task as explained above. The complete code has been attached in the appendix below.

[Link to another page](./another-page.html).

# Narrative Overview of Project 

When we decided upon building this project, neither of us had designed a game before. Hence, we knew it would be a demanding task of delivering a perfect gaming experience that involved assembling components that have never been used before by any of the versions available online. However, we took this up as a challenge and started building this project. We tackled our project in slots. We first programmed the RP2040 PICO microcontroller to test the 10 illuminating arcade buttons. We then integrated the code for the TFT display and printing of score for a single player to check if the TFT display was showing the right score upon pressing the illuminating arcade button. We then integrated the code for the second player and checked if the game was working for 2 players when they pressed the illuminating arcade buttons in unison. We then integrated the code for the LED Matrix as we wanted a better display to showcase the scores. We then integrated the code for the TFT display to guide the players by providing instructions. Then to complete the arcade gaming experience, we incorporated the code for a speaker module with custom built music notes that would play to indicate the commencement and the conclusion of the game. After we had the game in place, our next focus was to take care of the power requirement of the arcade buttons as they required a 5V supply. Hence, we chose to use a port expander which would not only give access to more number of GPIO pins but also provide a 5V supply. When we decided upon building this project, neither of us had designed a game before. Hence, we knew it would be a demanding task of delivering a perfect gaming experience that involved assembling components that have never been used before by any of the versions available online. However, we took this up as a challenge and started building this project. We tackled our project in slots. We first programmed the RP2040 PICO microcontroller to test the 10 illuminating arcade buttons. We then integrated the code for the TFT display and printing of score for a single player to check if the TFT display was showing the right score upon pressing the illuminating arcade button. We then integrated the code for the second player and checked if the game was working for 2 players when they pressed the illuminating arcade buttons in unison. We then integrated the code for the LED Matrix as we wanted a better display to showcase the scores. We then integrated the code for the TFT display to guide the players by providing instructions. Then to complete the arcade gaming experience, we incorporated the code for a speaker module with custom built music notes that would play to indicate the commencement and the conclusion of the game. After we had the game in place, our next focus was to take care of the power requirement of the arcade buttons as they required a 5V supply. Hence, we chose to use a port expander which would not only give access to more number of GPIO pins but also provide a 5V supply. 

# Troubleshooting of Issues 

We faced a lot of issues while designing this game. We would be listing all the issues so that it gives a fair idea to you people about the issues that you might face while replicating this project. We will also be listing the solutions that we came up with while resolving these issues. However, you people can come up with better alternatives.

First issue:

Since our game involved the usage of 11 arcade buttons we knew this would involve a massive amount of wiring. As electrical engineers we wanted our circuitry to involve minimal and clean connections so as to make the hardware easy to debug. Hence, we researched a lot and found out about these I2C breakout boards which would eliminate half the amount of wires which we would have otherwise ended up using had we not thought of this solution.

Second issue:

The introduction of these I2C breakout boards gave rise to another issue which is that they had predined I2C addresses. Since we were planning to allocate 4 arcade buttons to 2 I2C breakout boards and 3 arcade buttons to 1 I2C breakout board, we needed them to have different I2C addresses so that pin definition in the code would be easy. As a solution to this problem, we decided to cut the PCB trace of 2 of the I2C breakout boards so that each group of arcade buttons assigned to a single I2C breakout board would have a different I2C address and would still be able to use the predefined pins. This solution resolved our dilemma of using 11 arcade buttons.

Third issue:

The usage of 11 arcade buttons introduced the issue that not a single Adafruit Seesaw framework could be used to control all 11 arcade buttons as the 11 arcade buttons would be carrying out different tasks at the same time. We resolved this issue by assigning a group of arcade buttons to a single framework and having 3 frameworks provide parallel I2C support. 

Fourth issue:

We wanted the different events happening in our game to be executed at the same time. While building our game we realized that a lot of delay would be introduced if we let different functions be executed one after the other as they would become dependent on each other. Thus, we came up with the solution of using multicore functionality which allowed the execution of all individual events simultaneously. This eliminated delay completely thus providing a perfect gaming experience.

Fifth issue:

The arcade buttons we used required a 5V power supply to be able to illuminate light to their full potential. However, by just using the RP2040 PICO microcontroller we were able to only provide a 3V power supply which was not sufficient. We resolved this issue by using a port expander that provided a 5V supply. The usual approach would have been to build a power management circuitry but our thought process was to come up with a solution that took care of another possible issue which we have spoken about in the next one.

Sixth issue:

We used the port expander to provide a 5V power supply to the arcade buttons and made the best use of this solution by gaining access to more GPIO pins. Thus, our smart work here took care of 2 major issues.

Seventh issue:

On the day of our midpoint check, we had presented the game with an enclosure made of MDF which on being laser cut had black ash on its edges. This was not giving our product a final polished look. We tackled this by replacing MDF with black acrylic which stood out well with the colorful arcade buttons and thus made our project look like a finished product. 

# Advantages of the Project

We came up with a design that we were sure that we would be able to deliver. We meticulously planned every detail keeping in mind our budget. We made sure that we used every component that we ordered and also that every component that we used provided a benefit. 

1) We came up with a design that we were sure that we would be able to deliver. We meticulously planned every detail keeping in mind our budget. We made sure that we used every component that we ordered and also that every component that we used provided a benefit. 

2) We made use of I2C breakout boards that allowed us to use multiple arcade buttons by chaining them to a single I2C connection. 

3) We made use of a port expander thus making more GPIO pins accessible and providing 5V power supply to the arcade buttons.

4) We incorporated 2 displays for showing the instructions and scores thus making it easier for the players to keep track of the various events happening during the game.

5) We enclosed our hardware in a casing thus making sure that the players would have a perfect gaming interface.

# PIO Functionality utilized in the Project 

PIO helps us to create our own interfaces from scratch. PIO is like a tiny processor that runs code separately from the main  Cortex-M0+. Hence it is independent of the CPU. RP2040 has 2 PIO blocks each having 4 state machines. They each have a set of 9 instructions which allow for a wide range of behavior and location changes of data. They are written in a special language for the PIO system on RP2040 that can then be embedded in the main code. Using PIO we can dedicate a state machine to implement the control protocol. Using PIO leaves the processor free as the PIO is an independent module. Pio gives a much deeper level of control. In our project we have used PIO for I2C communication.

# Accomplishments achieved in the Project

We are particularly proud of the different components that we used in our game that have never been used before. Right from using the RP2040 PICO microcontroller to the I2C breakout boards to the port expander, we utilized components that took care of many bugs that our game otherwise would have had. We are also proud of having used multicore functionality that took care of executing events simultaneously thus eliminating delay completely. On the final demo day, everyone enjoyed playing our game because of the seamless gaming experience we provided. The faculty was proud to see how we designed an enclosure giving our project a final finished product like look. As electrical engineers, making the hardware easy and clean to debug and giving the game a polished look was a feat that we are extremely proud to have achieved with strict time constraints. Building this game will indeed always be a memorable experience. To all the people going through our website, we would love to see you recreate our game. Thank you!! 
