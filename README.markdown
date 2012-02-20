PySIMBAD.py
===========
**version** 0.0.7
http://github.com/eaydin/PySIMBAD

About :
    This is a simple script, written in a simple manner.
    Just connects to the CDS-Simbad Astronomical Services and retrieves information parsing the HTML files.
    Can be used both as a Python module, or a standalone program.
    Still has a lot to do, I'll add some stuff when I have the time.

Dependency : Python 2.6.x

Usage :

   - Can be used as a standalone program.
     `PySIMBAD.py <object name>`
     This will output everything that can be retrieved about the object.
     Example :
     `PySIMBAD.py "bl cam"`
    
   - Also can be used as a Python module.
   
   Let's first import it.
   `>>> import PySIMBAD as sim`
   
   Now we build a link for our desired object name, and we assign it to an object name (here named as "star"),
   `>>> link = sim.buildLink("sirius")
   >>> star = sim.simbad(link)`
   
   Now let's see what we can do with it,
   
   `>>> dir(star)
   ['__class__', '__delattr__', '__dict__', '__doc__', '__format__', '__getattribute__', '__hash__', '__init__', '__module__', '__new__', '__reduce__', '__reduce_ex__', '__repr__', '__setattr__', '__sizeof__', '__str__', '__subclasshook__', '__weakref__', 'dec', 'fk4', 'fk5', 'flux', 'flux_num', 'gal', 'getCoord', 'icrs', 'mainType', 'names', 'names_num', 'objectTypes', 'page', 'ra', 'refs']`
   
   So we have an attribute named fk5. Let's see what it does!
   
   `>>> print star.fk5()
   06 45 08.917 -16 42 58.02
   >>> print star.ra.__doc__
   Returns a string RA joined by ':'
   >>> print star.ra(star.fk5())
   06:45:08.917`
   
   Or we can just select the main type of the object (whether it's a galaxy, an asteroid, a supernova etc.)
   
   `>>> print star.mainType()
   Spectroscopic binary
   
   How about the flux information?
   
   >>> print star.flux.__doc__
   Returns a dictionary of Fluxes according to their Colors.
		Example :
		>>> S.flux()
		{'H': '-1.391', 'J': '-1.391', 'B': '-1.46', 'K': '-1.390', 'V': '-1.47'}
		>>> S.flux()['J']
		'-1.391'

   >>> star.flux()
   {'H': '-1.391', 'J': '-1.391', 'B': '-1.46', 'K': '-1.390', 'V': '-1.47'}`
   
   Well, here's the best part (and it's why I started building it in the first place)

   >>> for i in star.names() : print i
    ...
    NAME SIRIUS A
    GEN# +1.00048915A
    2MASS J06450887-1642566
    SAO 151881
    * alf CMa A
    GJ 244 A
    N30 1470
    SBC7 288
    * 9 CMa
    HD 48915
    NAME Dog Star
    SBC9 416
    * alf CMa
    HGAM 556
    NAME SIRIUS
    SKY# 11855
    ADS 5423 A
    HIC 32349
    NLTT 16953
    TD1 8027
    BD-16 1591
    HIP 32349
    NSV 17173
    TYC 5949-2777-1
    CCDM J06451-1643A
    HR 2491
    8pc 379.21A
    UBV M 12413
    CEL 1368
    IDS 06408-1635 A
    PLX 1577
    UBV 6709
    Ci 20 396
    IRAS 06429-1639
    PMC 90-93 186
    USNO 816
    CSI-16 1591 1
    IRC -20105
    PM 06430-1639A
    uvby98 100048915 A
    1E 064255-1639.4
    JP11 1425
    PPM 217626
    WDS J06451-1643A
    FK5 257
    LFT 486
    RAFGL 1007
    Zkh 91
    GAT 474
    LHS 219
    ROT 1088
    GC 8833
    LPM 243
    RX J0645.1-1642
    GCRV 4392
    LTT 2638
    1RXS J064509.3-164241
    
   There you go, have fun...
