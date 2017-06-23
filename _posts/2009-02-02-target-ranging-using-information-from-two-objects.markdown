---

title: Target ranging using information from two objects
abstract: In an embodiment, an apparatus includes a detector, direction finder, receiver, and range finder. The detector is operable to detect a target, and the direction finder is operable to determine a first direction to the target from the apparatus. The receiver is operable to receive a second direction to the target from a remote object, and the range finder is operable to determine from the first and second directions a range of the target from the apparatus. For example, the apparatus may be a first fighter jet, and the remote object may be a second fighter jet. By using directional information from both the first and second jets, a computer system onboard the first jet may compute a range to the target from the first jet more quickly and more accurately than by using directional information from only the first jet.
url: http://patft.uspto.gov/netacgi/nph-Parser?Sect1=PTO2&Sect2=HITOFF&p=1&u=%2Fnetahtml%2FPTO%2Fsearch-adv.htm&r=1&f=G&l=50&d=PALL&S1=08081106&OS=08081106&RS=08081106
owner: BAE Systems Information and Electric Systems Integration Inc.
number: 08081106
owner_city: Nashua
owner_country: US
publication_date: 20090202
---
This application claims priority to U.S. Provisional Application Ser. Nos. 61 063 251 61 063 290 61 063 271 and 61 063 207 filed on Jan. 31 2008 which are incorporated by reference.

The invention was made with United States Government support under Contract No. N00019 02 C 3002. Accordingly the United States Government has certain rights in this invention.

This Summary is provided to introduce in a simplified form a selection of concepts that are further described below in the Detailed Description. This Summary is not intended to identify key features or essential features of the claimed subject matter nor is it intended to be used to limit the scope of the claimed subject matter.

In an embodiment an apparatus includes a detector direction finder receiver and range finder. The detector is operable to detect a target and the direction finder is operable to determine a first direction to the target from the apparatus. The receiver is operable to receive a second direction to the target from a remote object and the range finder is operable to determine from the first and second directions a range of the target from the apparatus.

For example the apparatus may be a first fighter jet and the remote object may be a second fighter jet. By using directional information from both the first and second jets a computer system onboard the first jet may compute a range to the target from the first jet more quickly and more accurately than by using directional information from only the first jet.

Geometrically speaking His the projection of the actual range not shown in from the jet to the target T in both the jet azimuth plane and in all earth azimuth planes because the jet is flying at a substantially level altitude i.e. is flying substantially parallel to the earth s surface. For purposes of discussion the jet azimuth plane is a plane that passes through the jet s fuselage from nose to tail and in which both of the jet s wings lie or to which both of the jet s wings are parallel. An earth azimuth plane is any plane that is parallel to the earth s surface or more precisely any plane that is perpendicular to a radius line of the earth. Therefore when the jet is flying at a level altitude the jet s azimuth plane is either coincident with or parallel to a selected earth azimuth plane depending on the altitude of the selected plane. That is if the altitude of a selected earth azimuth plane is the same as the level altitude of the jet then the jet azimuth plane can be said to be coincident with the earth azimuth plane but if the altitudes of the selected earth azimuth plane and the jet s azimuth plane are different then these planes are parallel to but not coincident with each other. It is sometime convenient to select the earth azimuth plane in which the target T lies as the earth azimuth plane for target ranging calculations.

Geometrically speaking the target T lies in an elevation plane which is perpendicular to the jet azimuth plane and which includes the straight line along which His measured. For example in this embodiment the elevation plane may be coincident with the page of .

Referring to the fighter jet typically includes a targeting system not shown in for detecting the target T and for determining R and H and potentially V. For example the targeting system may actively detect and range the target by transmitting a signal e.g. a radar signal that impinges upon and is reflected back to the jet by the target T and by receiving the reflected signal with a directional antenna not shown in . The targeting system may then determine and by analyzing the phase of the received signal at each of multiple elements of the antenna. Alternatively the targeting system may passively detect and range the target T by similarly analyzing a signal emitted by the target to determine and . Passive detection may be useful when the pilot of the fighter jet does not want to alert the target T to the jet s presence or when the target is a pop up target e.g. a hand held rocket launcher that is difficult or impractical to actively detect. Because such target detecting and ranging systems are known the details of such a system are omitted for brevity.

Referring again to although the target detecting and ranging system onboard the fighter jet can determine from and that the target T lines along a straight line path the system cannot determine from these angles alone a value for R H or V.

Therefore the targeting system onboard the jet needs additional information to determine at least one of R H and V. Once the targeting system determines at least one of these values it can determine the remaining ones of these values via a trigonometric identity such as the law of sines.

For example a targeting system employing passive detection may obtain this additional information by comparing a signature of a signal emitted from the target T with signal signatures that are stored in a database.

If the signature of the emitted signal matches a signature in the database then the targeting system may be able to identify the target T and may be able to retrieve from the database information describing the target and or the emitted signal.

For example if the database includes a plot of distance vs. signal to noise ratio SNR for the emitted signal then the targeting system may calculate Rby measuring the SNR of the emitted signal at the fighter jet and obtaining a value for Rfrom the plot.

But this technique for calculating Rmay require a significant processing time and thus the system may be relatively slow in providing an accurate value for R. Furthermore phenomena such as an atmospheric disturbance and multipath may render the measurement of Rtoo inaccurate for some applications regardless of the needed processing time. As an example of when ranging convergence and accuracy may be an issue there are some targets e.g. pop up targets that the targeting system may be unable to detect until the jet is practically on top of the target e.g. His ten or fewer nautical miles . This inability of the targeting system may be due to the target e.g. a rocket launcher not being activated until the jet is in sight or the target being hidden by a mountain or other object. At the speed that the fighter jet may be travelling toward the target T and the speed at which the target may be travelling toward the jet if the target is airborne the pilot may have only a few seconds to decide on the best course of action e.g. engage or evade the target so the convergence time and the accuracy of the ranging calculation may be an important factor in allowing the pilot sufficient time to make the best decision and to execute the corresponding maneuver.

Alternatively if the target detecting and ranging system determines that the target T is a type of ground based target e.g. a tank or rocket launcher then if the target is at sea level Vis substantially equal to the altitude of the fighter jet because the altitude is measured by an altimeter not shown in on board the jet the targeting system has access to the altitude. Once the targeting system has a value for V the system can calculate Hand Rusing the law of sines.

But depending on the terrain in the vicinity of the target T the target detecting and ranging system onboard the jet may be unable to assume that the target is at sea level. For example if the target T is located in a mountainous region then the target may be thousands of feet above or below sea level. And even if the targeting system has access to data representing the terrain in the vicinity of the target T processing this data to determine the height at which the target is located may be relatively time consuming inaccurate or both time consuming and inaccurate. And such slow or inaccurate processing may make this ranging technique unsuitable for certain applications as discussed above.

Referring to an embodiment of a multi jet technique for detecting and ranging the target T is discussed. Although steps of the technique are presented in a particular order it is understood that these steps may be performed in any other suitable order. Furthermore although the jet is discussed as ranging the target T for both the jets and it is understood that the jet may also range the target T for either of the jets. Furthermore to avoid confusion the target detecting and ranging system installed on the jet and the components of this system are referenced with a subscript 1 and the target detecting and ranging system installed on the jet and the components of this system are referenced with a subscript 2 .

This multi jet technique may be invoked when both of the target detectors and in the jets and detect the target T. Each detector and may detect the target in any suitable manner such as the manner discussed above in conjunction with .

Next the target detector onboard the jet types the target T. For example the target detector may determine the type of the target T e.g. hostile fighter jet missile based on the signature of a signal emitted by the target. Because techniques for typing a target are known a discussion of these techniques is omitted for brevity.

Then the jet transmits via its transceiver and antenna the target type that its target detector has determined for the target T.

Next the jet receives via its antenna and transceiver the target type transmitted by the jet and the target detector compares the two target types determined by the target detectors and .

If the two target types match then the target detector determines that both the jets and are attempting to range the same target T and allows the ranging of the target to proceed.

But if the two target types do not match then the target detector halts the ranging algorithm until such time as it determines that the jets and are attempting to range a same target.

If the target detector determines that both the jets and are attempting to range the same target T then the target direction finders and onboard the fighter jets determine the following quantities and D.

 is the azimuth angle between the heading of the jet and the target T and the direction finder may determine this angle by analyzing the phases of a signal received from the target by multiple elements of the first antenna . As discussed above in conjunction with this signal may be for example emitted by the target T or may be a radar signal reflected by the target.

Similarly is the azimuth angle between the heading of the jet and the target T and the direction finder may determine this angle in a manner similar to that used by the direction finder to determine 

 AZis the azimuth angle between the jet and the heading of the jet . The direction finder may determine this angle in a manner similar to the manner it uses to determine AZ. Alternatively the direction finder may receive via the antenna and transceiver from the jet or from another source e.g. a satellite or ground based tracking station the coordinates of the jet and therefore may calculate from the coordinates of the jets and using one or more trigonometric functions it is assumed that the direction finder has access to the coordinates of the jet in which it is installed.

Similarly is the azimuth angle between the jet and the heading of the jet . The direction finder may determine this angle in a manner similar to the manner in which the direction finder determines .

D is the straight line distance between the jets and and is defined along a line that is at the angle from the heading and that is at the angle from the heading . For example the target direction finder may calculate D from the coordinates of the jets and .

Next the jet transmits via the antenna and the transceiver the values of and to the jet and the target range finder receives these values via the antenna and the transceiver .

Then the target range finder on board the jet calculates angles A and B according to the following equations where A and B are interior angles of a triangle with vertices at the jet the jet and the target T 1 2 

Next the target range finder calculates the interior angle C of the triangle according to the following equation 180 3 

Then the target range finder calculates Haccording to the following equation which is derived from the law of sines 

Because the jets and and the target T lie in the same plane in this embodiment the actual range Requals H.

Still referring to the target direction finders and may compute the values of the azimuth angles TARGET TARGET and with respective errors in respective known error ranges and these errors may introduce errors into the values that the target range finder computes for angles A and B.

And these errors in the angles A and B may introduce errors into the values that the target range finder calculates for Hand H.

It is sometimes useful to provide the pilot of a fighter jet such as the jet or with the percentage range error PRE of the range values Hand Hso that the pilot may determine the range window of a target. This range window may give the pilot enough information to decide on what action to take relative to the target e.g. engage or evade . For example a missile on board the jet may have a maximum range of ten nautical miles NM . Therefore if the target range finder provides H 9 NM and PRE 10 then the pilot can determine that the maximum value of H 9 0.01 9 NM 9.9 NM and therefore that the target T is within the range of the missile.

Assuming that the sigma value the standard deviation from the correct value for the angle A equals or is approximately equal to the sigma value for the angle B then the target range finder may calculate PRE according to either one of the following two equations 

And where is not approximately equal to then the target range finder may calculate PRE according to the following equation 

Because the jets and and maybe the target T are moving relative to one another the targeting system may continuously update the values of H H and PRE for example every second or every few seconds until the target is destroyed successfully evaded or out of range.

Still referring to alternate embodiments of the described target detecting and ranging technique are contemplated. For example although the jet is described as calculating Hand H the jet may calculate these values both jets may calculate these values or the jet may calculate Hand the jet may calculate H. Furthermore one or both of the jets and may be other objects or vehicles such as a satellite a tank a helicopter a water vessel a balloon or a missile or other projectile. Moreover if there are multiple targets T then the system may range each of these targets in a similar manner. In addition although the target T is shown in front of both of the jets and the above described detecting and ranging technique may be used regardless of the location of the target as long as the jets and target do not lie along the same straight line. But because the jets and are moving relatively quickly it is unlikely that the target T and the jets will lie along the same straight line for any significant period of time. Therefore the target range finder may continue ranging the target T according to the above described technique as soon as the target and jets and again form the vertices of a triangle such as the triangle . Furthermore although described as a single antenna each of the directional antennas and may include multiple antennas such as multiple short base inferometer SBI antennas that together provide data sufficient for the target direction finders and to determine the angles and . Moreover although the triangle is described as lying in an earth azimuth plane the detecting and ranging technique may be used regardless of the plane in which the triangle lies.

Furthermore because in this embodiment R Hand R H a technique for calculating Rand R not shown in is discussed below in conjunction with .

Referring to the target range finder onboard the jet may calculate the azimuth distance D between the jets and in a variety of ways. For example if the range finder receives the XYZ coordinates of the jets and then the range finder may calculate D X X. Alternatively the range finder may determine a projected distance S between the jets from the coordinates determine the vertical distance V as the difference between the altitudes of the jets and and then solve for D using the Pythagorean Theorem. Or the target systems and of the jets and may determine the distance S for purposes of this calculation S is the actual distance between the jets and projected onto an elevation plane that also contains D and V or the distance V determine the angles and and calculate D using the law of sines.

H V and Rform a right triangle in a first elevation plane and H V and Rform a right triangle in a second elevation plane. For purposes of illustration both of these elevation planes are overlaid onto a single elevation plane that is parallel or coincident with the plane in which lies.

Next the target direction finders and respectively determine the elevation angles and in a manner that may be similar to the manner in which the direction finders determine the azimuth angles and of .

The range finder may also calculate a PRE for Rand Rby taking into account the PRE of Hand Hand the sigmas for and .

Still referring to other embodiments for calculating Rand Rare contemplated. For example referring to and the range finder may determine a distance P between the jets and in a manner similar to that used to calculate the distance D FIG. P is the projection of S the actual distance between the jets and onto the elevation plane onto which the above described first and second elevation planes are overlaid may calculate angles W and Z from and in a manner similar to that used to calculate angles A and B from and of and may calculate U R and Rin a manner similar to that used to calculate C H and Hof . Or the range finder on board the jet may calculate R R or both of these values.

Referring to alternate embodiments of the ranging techniques are contemplated. For example although the target T is shown at an altitude that is between the altitudes of the jets and T may have any altitude or be ground based. Furthermore T may have any azimuth location relative to the jets and . Moreover because His often more useful to a pilot than R the target systems and onboard the jets and may calculate only Hand H. In addition any alternatives discussed above in conjunction with may also be applicable to the embodiments of .

From the foregoing it will be appreciated that although specific embodiments have been described herein for purposes of illustration various modifications may be made without deviating from the spirit and scope of the disclosure. Furthermore where an alternative is disclosed for a particular embodiment this alternative may also apply to other embodiments even if not specifically stated.

