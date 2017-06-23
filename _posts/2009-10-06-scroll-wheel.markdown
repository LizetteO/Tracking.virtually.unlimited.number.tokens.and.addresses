---

title: Scroll wheel
abstract: The invention relates to a method for enabling scrolling on a display in a first direction by turning a scroll wheel of a computer mouse without the need to lift a finger from the scroll wheel during scrolling. This is obtained by switching the mode of operation of the scroll wheel from a first mode of operation, mode 1, to a second mode of operation, mode 2, by performing an action, such as holding down a specific key. The program procedure for mode 2 is such that when the scroll wheel is first turned upon switching to mode 2, a first direction of turning is de-fined. Continued turning of the scroll wheel in either the first direction of turning or another direction of turning will cause a scrolling on the display in the first direction.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08350811&OS=08350811&RS=08350811
owner: 
number: 08350811
owner_city: 
owner_country: 
publication_date: 20091006
---
This application is an U.S. national phase application under 35 U.S.C. 371 based upon co pending International Application No. PCT DK2009 050266 filed on Oct. 6 2009. Additionally this U.S. national phase application claims the benefit of priority of co pending International Application No. PCT DK2009 050266 filed on Oct. 6 2009 and Denmark Application No. PA 2008 01403 filed on Oct. 6 2008. The entire disclosures of the prior applications are incorporated herein by reference. The international application was published on Apr. 15 2010 under Publication No. WO 2010 040358.

The present invention relates to the functioning of a scroll wheel. The meaning of the term scrolling on a computer screen or other type of display is well known. The most common use of scroll wheels is as part of computer mice but it is also used on certain types of control panels. Turning of a scroll wheel usually effects vertical scrolling. Left or right scrolling can sometimes be effected by pushing the scroll wheel left or right respectively. Often a scroll wheel will have a built in click button that can be customized to perform a desired action.

For known scroll wheels turning the scroll wheel in a downward direction towards the user results in an upward motion of content displayed on the display and vice versa. This works well for short and slow scrolling. To keep down costs a standard scroll wheel is usually made out of plastic and sometimes has a rubber rim. Such a wheel has a small weight and thus a small moment of inertia. The bearing friction in such a wheel is also somewhat high another result of low cost manufacturing. Such a wheel is not well suited for so called free spin where the wheel can rotate many times before stopping due to friction. Even when the wheel is rotated quickly initiated with a quick motion of the finger it will stop before achieving a 360 degree rotation. Scrolling through a large document thus has to be performed by repeatedly turning the wheel and lifting one s the finger. This is uncomfortable and inefficient. A wheel made partly of metal and with bearings designed for low friction can allow some amount of free spin and thus fast scrolling. However this is a costly solution partly due to the somewhat high cost of a metal wheel and partly due to a higher cost of manufacturing bearings having the required low friction. Furthermore most people prefer that the scroll wheel is capable of scrolling in small well defined steps enabling for instance scrolling in steps of one half line in a word processing software program. If the wheel is to be able to perform free spin there must be a built in motor that can disable this functionality at high rotation speeds. Computer mice with such functionality do exist. They typically consist of some hundred single parts and the result is that manufacturing costs are double or more compared to standard computer mice. Because of the high price computer mice having free spin capability are not very common. Another reason is that when using free spin one may lose the feeling of the amount of scrolling that is taking place.

The present invention changes the functionality of a traditional scroll wheel in such a way that contrary to known ways the scroll wheel becomes advantageous for scrolling at both slow and medium speeds.

The invention can build upon a known scroll wheel that is neither construction wise nor with respect to otherwise built in functionally is designed for fast scrolling. According to the invention the scroll wheel has two separate modes of operation mode 1 and mode 2. The first mode of operation mode 1 it works like a standard scroll wheel where the direction of scrolling is related to the direction in which the scroll wheel is turned. According to the invention a user can switch to a second mode of operation mode 2 of the scroll wheel by performing an action. In mode 2 the direction of scrolling depends on a first direction of turning of the scroll wheel upon changing the mode of operation to mode 2. Subsequent turning of the scroll wheel in either direction will result in scrolling in the direction that the first direction of turning of the scroll wheel would cause in the standard mode of operation mode 1 . The scroll wheel is returned to mode 1 by the same or a different action than that used for switching the scroll wheel to mode 2.

The invention thus enables an inexpensive scroll wheel to be suitable for scrolling at medium speed. It is medium speed scrolling that most needs improving since long scrolling in any event is most easily performed using scroll bars on the display this is a well known method. What renders a standard scroll wheel not suitable for medium speed scrolling is as previously mentioned that it requires continuously turning the scroll wheel then lifting of the finger then turning the scroll wheel again and so on. This is mediated by the functionality provided by the invention only forward and backward turning of the scroll wheel are necessary in mode 2 not lifting of the finger. Furthermore it can prevent the loss of sense for how much scrolling one has incurred.

As mentioned the invention allows a user to switch between to different modes of operation of the scroll wheel.

Method 1 Switching from mode 1 to mode 2 happens when a key is pressed and held and switching back to mode 1 happens when the same key is released.

Method 2 Switching to mode 2 happens when a key is pressed. Switching back to mode 1 happens by pressing the same or a different key.

Method 3 Switching to mode 2 happens when the scroll wheel s click button is pressed. Switching back to mode 1 happens when the scroll wheel s click button is pressed again.

Method 4 Switching to mode 2 happens as described in one of methods 2 or 3 and switching back to mode 1 happens when the mouse is moved more than a predetermined distance.

Addition 1 For a given speed of rotation of the scroll wheel the scrolling is faster in mode 2 than in mode 1.

Addition 2 If the scroll wheel is of a kind that can be tilted then horizontal scrolling in mode 2 is faster than in mode 1.

Mode 1 corresponds to scrolling in accordance with known principles. In mode 2 programming is adapted so that the scroll wheel operates in accordance with the invention.

In mode 1 scrolling occurs in accordance with known principles i.e. the scrolling on the display reflects the direction of turning of the scroll wheel.

Given the information in this specification a person skilled can implement the invention since the invention to a large extent can employ known program procedures. An example that in a very simplified manner reflects the invention i.e. implements mode 1 and mode 2 and the switching between the two modes looks like this 

The pseudo code is by and large selfexplanatory. The function  display scroll in the subroutine  display scrolling is a pseudoname for the function that causes the actual scrolling of the image on the display. This function is typically accessible via the application programming interface API of the program in which the user wishes to perform scrolling.

 action go to mode2 i.e. the action that is performed to switch from mode 1 to mode 2 can for instance be to press and hold a key. The action action go to mode1 that is performed to switch from mode 2 to mode 1 could be to release the key again. This method was described previously.

Implementation of the other functionalities described herein is just as straightforward for a person skilled in the art.

