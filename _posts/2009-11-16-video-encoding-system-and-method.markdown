---

title: Video encoding system and method
abstract: A video encoding system for encoding consecutive images, the encoding of a current image being done with respect to a previous and/or subsequent image, the encoding system including a reception module to receive the current image to be encoded and to receive a non-estimated real motion vector of a moved area of the current image; a divider to divide the current image into macroblocks; a module to estimate motion vectors depending on the macroblocks of the current image and on the previous and/or subsequent image; a motion compensation module to receive motion vectors and to provide a predicted area; a module to allocate the non-estimated real motion vector to the macroblocks belonging to the moved area; a module to transmit the non-estimated real motion vector directly to the motion compensation module without any estimation of the motion vectors by the estimation module for macroblocks belonging to the moved area.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08731060&OS=08731060&RS=08731060
owner: Sagemcom Broadband SAS
number: 08731060
owner_city: Rueil-Malmaison
owner_country: FR
publication_date: 20091116
---
This application is the U.S. National Stage of PCT FR2009 052193 filed Nov. 16 2009 which in tuna claims priority to French Patent Application No. 0859113 filed Dec. 30 2008 the entire contents of all applications are incorporated herein by reference in their entireties.

The present invention relates to a video encoding system. It also has as an object a video encoding method. The invention can be used in the field of video data broadcasting from a server to a client terminal. The server which is generally a computer is connected to the client terminal such as for example a video decoder through a network for example a High Definition Multimedia Interface HDMI WIFI or Ethernet type network. In this way the computer screen may be displayed by the client terminal on a TV screen according to a Remote Frame Buffer type protocol for example VNC Virtual Network Computing protocol.

In such architecture the server encodes that is compresses what it broadcasts before sending it to the client terminal. If the server had to display on an own screen the images it broadcasts their compression would not be necessary. To perform compressing the server carries out a capture of its own display codes it and sends it through the network to the client terminal. Each image to be displayed is stored in a buffer known as framebuffer of the server and is generally coded in an RGB format Red Green Blue which constitutes the most direct manner to encode the images the three plans corresponding to the three elementary colors red green and blue. Then the image is generally transformed in a YUV format or luminance chrominance . The first plan called luminance plan Y represents the luminous intensity of the pixels. The two following plans correspond to the chrominance U V and carry the color information. There mainly exist two YUV formats 

The encoding carried out by the server is a space time type encoding such as a H264 encoding. The H264 standard is a video coding standard jointly developed by the VCEG Video Coding Experts Group and the MPEG Moving Pictures Experts Group . This standard makes it possible to encode video streams with a speed lower than twice less that obtained by the MPEG2 standard for the same quality. A space time encoding encodes integrally only a portion of the images to be transmitted in order to reconstitute a video. The H264 standard includes the types of image known and defined in the MPEG2 standard namely 

However the implementation of such an encoding solution raises a number of difficulties when it comes to the real time transfer of the server display on the client terminal.

Thus such a coding mode is very much consuming in terms of time and of computation means. To save band width the data must be compressed as much as possible. This important compression imposes a great complexity in terms of encoding. Thus the server must not only carry out image compression but also carry out several computations to determine the addresses and the data to be encoded. This energy overconsumption makes the implementation of other applications running on the same server delicate.

In this context the aim of the present invention is to provide a space time video encoding system making it possible to reduce the encoding load for a use according to a real time client server protocol while leaving enough resources on the server dealing with the encoding for running other applications.

To this end the aim of the invention is to provide a video encoding system for encoding consecutive images of a video sequence the encoding of at least one current image being operated with respect to at least one previous and or subsequent image of said video sequence said encoding system comprising 

said encoding system being characterized in that said data reception module further receives a non estimated real motion vector of at least one moved area of said current image said encoding system including 

The term macroblock refers to an elementary rectangular area of the image having a size comprised between 4 4 and 16 16 pixels while going through 8 16 8 8 pixels . . . . Each macroblock being itself composed of luminance blocks and chrominance blocks.

The motion estimation during a space time encoding is an operation which requires a very high computing power. The system according to the invention makes it possible to avoid part of this estimation by advantageously using the provision of an already existing motion vector.

Thanks to the invention the provision of the motion vector relating to an area typically a rectangle inside an image or frame having undergone a displacement makes it possible not to calculate the motion vectors for the macroblocks which are located in such a moved area. The real motion vector is directly injected at the input of the compensation module.

Interestingly the encoding system may be used in the case where initiation of the area displacement is carried out at a client terminal connected to a server via a VNC protocol the terminal screen displaying the rendering of the displacement. Encoding by the system according to the invention is carried out at the server and the real vector of the displaced area is provided by a programming interface of the server graphical environment.

In addition to the reduced encoding load it will be appreciated that thanks to the invention the rendering will be improved since real and not estimated motion vectors are at least partly used.

Typically such a real motion vector for an area undergoing a displacement may be obtained in the frame of applications such as 

The system according to the invention may also have one or more of the characteristics below considered individually or in any technically possible combination 

Another object of the present invention is a video encoding method for encoding consecutive images of a video sequence the encoding of at least one current image being operated with respect to at least one previous and or subsequent image of said video sequence said method comprising the steps of 

said current image to be encoded being transmitted from a server to a client terminal the encoding being carried out at the server and said non estimated real vector of at least one moved area of said current image being provided by a programming interface of the graphical environment of said server.

The method according to the invention may also have one or more of the characteristics below considered either individually or according to all technically possible combinations 

The invention may be used in the field of video data broadcasting from a server to a client terminal. The server which is generally a computer is connected to the client terminal for example a video decoder through a network for example a High Definition Multimedia Interface HDMI WIFI or Ethernet type network. Consequently the computer screen may be displayed by the client terminal on a TV screen according to a Remote Frame Buffer type protocol for example a Virtual Network Computing VNC protocol. The server encodes what it broadcasts before sending it to the client terminal. The encoding carried out by the server is a space time type encoding such as H264 encoding thus it is the server which incorporates the encoding system according to the invention.

The reception module is inputted with a predictive image F. Fcorresponds to the current image of the screen of the server in its entirety. It should be noted that the invention only relates to the encoding of the predictive images the intra predictive encoding of images being proceeded with according to known techniques. Thus for the sake of clarity of the drawing the means required for the intra predictive encoding have been voluntarily omitted.

The reception module is also inputted with information relating to the areas that have gone through a displacement also referred to as moved areas hereinafter in the Fimage. The moved area is a rectangular area generally represented by a quadruplet x y l h x and y respectively represent the abscissa and the ordinate of the top left point of the area l represents the width of the rectangle and h is the height thereof. The information received by the server concerning each moved area is composed of the real motion vector m mx my of this moved area mx and my being the horizontal and vertical components of the real motion vector and T designating the transposition operator. Typically this real vector may be obtained by the server via the programming interfaces of its graphical environment also known as API Application Programming Interfaces or GUI Graphical User Interface of the software application running on the server and used by the client terminal or the operating system of the server for example Windows .

This real motion vector is known to the software application since the latter is behind the origination of the displacement of the area as a result of an event typically an event brought about by a mouse click or a keystroke of the end user via the client terminal.

However in order to have the scale of this vector to calculate it in number of pixels it might be necessary to reach the API of lower software layers. Thus the system will preferably rely on the operating system Windows layer to recover the real vector in order to implement this encoding software accelerator regardless of the applications which will benefit therefrom. By way of example a JavaScript function of windows.scrollby x coord y coord type of DOM Windows may be called upon which will be called upon when a downwards arrow key on the client terminal is pressed the function can provide the module of the motion vector 

The size of the rectangle can also be obtained by windows.innerHeight type and windows.innerWidth type functions.

In any event the server may obtain values characterizing the real motion vector of the area moved by the user via the client terminal.

Typically such a real motion vector for an area undergoing a displacement may be obtained in the frame of applications such as 

Thus a whole portion of the motion vector computations for the macroblocks to which module has already allocated a real motion vector because of their belonging to a moved area is saved.

Thus each current image Fto be encoded is divided by means into macroblocks corresponding to an elementary rectangular area of the image having a variable size comprised between 4 4 and 16 16 pixels going through 8 16 8 8 pixels . . . .

Means knowing the moved areas of the Fimage as well as their real motion vectors make it possible to allocate to the macroblocks belonging to a moved area a same real motion vector. Consequently means will direct only the macroblocks not touched by a moved area towards the motion estimation module the real motion vectors of the others macroblocks being directly transmitted to the motion compensation module via means .

The function of the motion estimation module is to find a macroblock of the current image Fin at least a previous image Fof the server screen in its entirety it could also be a subsequent image in the case of a B image and even of a plurality of previous and or subsequent images . When part of a previous image which resembles according to a least squares criterion for example the macroblock is found a motion vector which corresponds to the difference between the position of the selected area and that of the macroblock is deduced therefrom.

The motion vectors which were retained by the estimation module besides the real motion vectors transmitted by means are transmitted towards the motion compensation module . Thus a prediction error due to the fact that the retained area in the last image is not exactly equal to the analyzed macroblock is obtained. At the output of the motion compensation module a predicted image P is obtained.

A frequency transform Discrete Cosine Transform DCT type or Hadamard transform type is applied via the frequency transform module to each macroblock that have undergone a motion estimation as well as on the residual error D. This transform makes it possible to have a frequency representation of the modified areas.

The data from the frequency transform module are then quantified i.e. encoded on a limited number of bits by the quantification module to provide transformed and quantified parameters X. The function of the quantification module is to define different quantification steps according to whether certain components will be judged to be visually significant or not these quantification steps are defined in a quantification step table.

The reverse quantification module recovers the transformed and quantified parameters X which then traverse the reverse frequency transform module which operates a reverse frequency transform to recover a quantified version D of the residual error D this quantified version D is then added to the macroblocks of the predicted area P by adder the image outputted from adder is then processed by the release filter to provide a rebuilt image F corresponding to a set of rebuilt areas having the same position the same width and the same height as the modified areas. F is internally used by decoder to estimate the quality of the encoding.

The quantified results X from the quantification module are then reordered by the reordering module to group the non null coefficients together so as to allow an effective representation of the other coefficients having a null value.

The data then undergo a last phase of entropic coding compression via the entropic encoder . The function of the entropic encoder is to re encode differently the data so as to decrease the number of bits necessary to their encoding by approaching as closely as possible the minimum of theoretical bits which is fixed by the entropy .

The entropic encoder builds an output flow in a Network Abstraction Layer NAL format defined to allow the use of the same video syntax in various network environments.

It will be noted that the means and modules described above can be either software or made from specific electronic circuits.

In particular the invention was more particularly described within the framework of the H264 coding but it may be used in any type space time coding which is for example the case for MPEG2 or VC1 coding a video compression standard of the Society of Motion Picture and Television Engineers SMPTE .

Moreover it should be noted that the motion vector has been described as a two dimensional vector but it is also possible to use a three dimensional motion vector for example in the case of a graphic interface such as Aero which is the graphic interface of Windows Vista allowing the display of 3D effects.

