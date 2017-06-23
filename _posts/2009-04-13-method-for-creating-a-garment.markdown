---

title: Method for creating a garment
abstract: A method of creating a garment. The method comprises the steps of: (a) capturing an image of a person using a camera; (b) selecting a card having a depiction of a garment and encoded information relating to the garment depicted; (c) optically reading the encoded information on the card; (d) manipulating the captured image in accordance with the encoded information; (e) generating print data for garment pieces using the encoded information and the manipulated image; (f) communicating the print data to a garment fabric printer; and (g) printing outlines of garment pieces and a decorative finish on to a surface of a bolt of fabric.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=07965416&OS=07965416&RS=07965416
owner: Silverbrook Research Pty Ltd
number: 07965416
owner_city: Balmain, New South Wales
owner_country: AU
publication_date: 20090413
---
The present application is a continuation of U.S. application Ser. No. 11 525 862 filed Sep. 25 2006 which is a continuation of U.S. application Ser. No. 10 326 308 filed Dec. 23 2002 now abandoned which is a continuation of U.S. application Ser. No. 09 112 759 filed on Jul. 10 1998 now abandoned the entire contents of which are herein incorporated by reference.

The following co pending US patent applications identified by their US patent application serial numbers USSN were filed simultaneously to the present application on Jul. 10 1998 and are hereby incorporated by cross reference

The present invention relates to an image processing method and apparatus and in particular discloses a Garment Design and Printing System.

The present invention further relates to the creation of fabrics and garments utilising automated apparatuses.

A number of creative judgements are made when any garment is created. Firstly there is the shape and styling of the garment and additionally there is the fabric colours and style. Often a fashion designer will try many different alternatives and may even attempt to draw the final fashion product before creating the finished garment.

Such a process is generally unsatisfactory in providing a rapid and flexible turn around of the garments and also providing rapid judgement of the final appearance of a fashion product on a person.

It is an object of the present invention to provide an alternative form for analysing the look of garments and for their creation. A further object of the present invention is to provide for automatic fabric creation.

In accordance with the first aspect of the present invention there is provided A garment creation system comprising 

an expected image creation system including an image sensor device and an image display device said image creation system mapping portions of an arbitrary image sensed by said image sensor device onto a garment and outputting on said display device a depiction of said garment 

a garment fabric printer adapted to be interconnected to said image creation system for printing out corresponding pieces of said garment including said mapped portions.

The preferred embodiment is preferably implemented through suitable programming of a hand held camera device such as that described in co pending U.S. patent application Ser. No. 09 113 060 entitled Digital Instant Printing Camera with Image Processing Capability Docket ART01 filed concurrently herewith by the present applicant the content of which is hereby specifically incorporated by cross reference.

The aforementioned patent specification discloses a camera system hereinafter known as an Artcam type camera wherein sensed images can be directly printed out by an Artcam portable camera unit. Further the aforementioned specification discloses means and methods for performing various manipulations on images captured by the camera sensing device leading to the production of various effects in an output image. The manipulations are disclosed to be highly flexible in nature and can be implemented through the insertion into the Artcam of cards having encoded thereon various instructions for the manipulation of images the cards hereinafter being known as Artcards. The Artcam further has significant onboard processing power provided by an Artcam Central Processor unit ACP which is interconnected to a memory device for the storage of important data and images.

The aforementioned patent specification discloses an Artcam system as indicated in . The Artcam system relies on an Artcam which takes Artcards as an input. The Artcard includes encoded information for manipulation of an image scene so as to produce an output photo which contains substantial manipulation in accordance with the instruction of Artcard . The Artcards are designed to be extremely inexpensive and contain on one surface the encoding information and on the other surface a depiction of the likely effect which will be produced by the Artcard when inserted in Artcam .

In accordance with the method of the preferred embodiment as shown in a large number of Artcards are prepared and distributed in packs . Each pack relates to clothing wear of a specific size and includes images eg. of models having clothing apparel on to which an image captured by the camera will be mapped. The mapping can be to different items of apparel on different Artcards . One form of mapping algorithm is as illustrated in wherein the input image is first warped utilising a warp map which maps the image to a repeating tiling pattern that produces attractive warping effects. Of course many other forms of algorithms could be provided for producing an attractive form of material with the algorithm being provided on Artcard .

Next a second warp is provided for warping the output of first warp map onto the specific model image in the Artcard. Therefore warp will be Artcard specific. The result can then be output for printing as an art photo . Hence a user is able to point an Artcam at a design image and produce art photo which has a manipulated version of the image based upon a model s item of fashion apparel or garment. This process can be continued until a desirable result is produced.

Next as indicated in when a final selection has been made the Artcam can be connected by its USB port as illustrated at to a fabric printer which can comprise an ink jet fabric printer and associated drive controller electronics etc. The printer comprises a printhead having a width corresponding to the width of a bolt of fabric. Either the Artcam or the ink jet printer can be programmed to print out on fabric the garment pieces eg. having on the surface thereof the original warped image so as to produce a garment corresponding to that depicted by the model on the Artcard.

The output fabric can include tab portions eg. for alignment and border regions eg. in addition to instructions for joining the garment pieces together. Preferably the output program includes providing for warp matching of border regions so as to present a continuous appearance on the garment cross seams. Additionally a user interface could be provided for utilising the same Artcard with many different output sizes so as to taken into account different shaped bodies. By utilisation of Artcam technology a system can be provided for customised production of garments and rapid depiction of the likely results by means of utilisation of the Artcam device .

It would be appreciated by a person skilled in the art that numerous variations and or modifications may be made to the present invention as shown in the specific embodiment without departing from the spirit or scope of the invention as broadly described. The present embodiment is therefore to be considered in all respects to be illustrative and not restrictive.

The embodiments of the invention use an ink jet printer type device. Of course many different devices could be used. However presently popular ink jet printing technologies are unlikely to be suitable.

The most significant problem with thermal ink jet is power consumption. This is approximately 100 times that required for high speed and stems from the energy inefficient means of drop ejection. This involves the rapid boiling of water to produce a vapor bubble which expels the ink. Water has a very high heat capacity and must be superheated in thermal ink jet applications. This leads to an efficiency of around 0.02 from electricity input to drop momentum and increased surface area out.

The most significant problem with piezoelectric ink jet is size and cost. Piezoelectric crystals have a very small deflection at reasonable drive voltages and therefore require a large area for each nozzle. Also each piezoelectric actuator must be connected to its drive circuit on a separate substrate. This is not a significant problem at the current limit of around 300 nozzles per print head but is a major impediment to the fabrication of pagewidth print heads with 19 200 nozzles.

Ideally the ink jet technologies used meet the stringent requirements of in camera digital color printing and other high quality high speed low cost printing applications. To meet the requirements of digital photography new ink jet technologies have been created. The target features include 

All of these features can be met or exceeded by the ink jet systems described below with differing levels of difficulty. Forty five different ink jet technologies have been developed by the Assignee to give a wide range of choices for high volume manufacture. These technologies form part of separate applications assigned to the present Assignee as set out in the list under the heading Cross References to Related Applications.

The ink jet designs shown here are suitable for a wide range of digital printing systems from battery powered one time use digital cameras through to desktop and network printers and through to commercial printing systems

For ease of manufacture using standard process equipment the print head is designed to be a monolithic 0.5 micron CMOS chip with MEMS post processing. For color photographic applications the print head is 100 mm long with a width which depends upon the ink jet type. The smallest print head designed is covered in U.S. patent application Ser. No. 09 112 764 which is 0.35 mm wide giving a chip area of 35 square mm. The print heads each contain 19 200 nozzles plus data and control circuitry.

Ink is supplied to the back of the print head by injection molded plastic ink channels. The molding requires 50 micron features which can be created using a lithographically micromachined insert in a standard injection molding tool. Ink flows through holes etched through the wafer to the nozzle chambers fabricated on the front surface of the wafer. The print head is connected to the camera circuitry by tape automated bonding.

The present invention is useful in the field of digital printing in particular ink jet printing. A number of patent applications in this field were filed simultaneously and incorporated by cross reference.

Eleven important characteristics of the fundamental operation of individual ink jet nozzles have been identified. These characteristics are largely orthogonal and so can be elucidated as an eleven dimensional matrix. Most of the eleven axes of this matrix include entries developed by the present assignee.

The complete eleven dimensional table represented by these axes contains 36.9 billion possible configurations of ink jet nozzle. While not all of the possible combinations result in a viable ink jet technology many million configurations are viable. It is clearly impractical to elucidate all of the possible configurations. Instead certain ink jet types have been investigated in detail. Forty five such inkjet types were filed simultaneously to the present application.

Other ink jet configurations can readily be derived from these forty five examples by substituting alternative configurations along one or more of the II axes. Most of the forty five examples can be made into ink jet print heads with characteristics superior to any currently available ink jet technology.

Where there are prior art examples known to the inventor one or more of these examples are listed in the examples column of the tables below. The simultaneously filed patent applications by the present applicant are listed by USSN numbers. In some cases a print technology may be listed more than once in a table where it shares characteristics with more than one entry.

Suitable applications for the ink jet technologies include Home printers Office network printers Short run digital printers Commercial print systems Fabric printers Pocket printers Internet WWW printers Video printers Medical imaging Wide format printers Notebook PC printers Fax machines Industrial printing systems Photocopiers Photographic minilabs etc.

The information associated with the aforementioned 11 dimensional matrix are set out in the following tables.

