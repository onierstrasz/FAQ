# VisualWorks FAQ

*@What is the difference between packages, bundles and parcels?*
*@How do I load a parcel from the Visual Works Distribution?*
*@How do I get color sensitive editing?*
*@How can I change the RBCodeHighlight colours?*
*@What do I load to get the refactory browser?*
*@What do I load to have the SUnit buttons in the browser?*
*@What do I load to have the tabs in my browser?*
*@How do I open an SUnit TestRunner?*
*@How do I drag and drop a class or namespace definition from one package to another?*
*@How can you get the browser to show all methods when no protocol is selected?*
*@How do I interrupt a process?*
*@How do I modify the order in which packages belonging to a bundle are loaded?*

@What is the difference between packages, bundles and parcels?
<font color="green">What is the difference between packages, bundles and parcels?</font>
A <I>package</I> is a set of classes. A <I>bundle</I> is a set of packages and bundles. A <I>parcel</I> is a bunch of stuff that has been filed out.

@How do I load a parcel from the Visual Works Distribution?
<font color="green">How do I load a parcel from the Visual Works Distribution?</font>
On Visual Works do
   system > parcel manager 
   look  in VisualWorks > parcels
Select the parcel you wish to load and load it by right mouse clicking on the parcel.

@How do I get color sensitive editing?
<font color="green">How do I get color sensitive editing?</font>
Load the RBCodeHighlighting package from SCG Store.

@How can I change the RBCodeHighlight colours?
<font color="green">How can I change the RBCodeHighlight colours?</font>
Browse the class <tt>CodeHighlightingSettings</tt>.
Select the class method <tt>windowSpec</tt>.
Click on the <I>visual</I> tab and open it.

@What do I load to get the refactory browser?
<font color="green">What do I load to get the refactory browser?</font>
The refactoring browser is loaded in the default image. It is obtained by System/Browse.

@What do I load to have the SUnit buttons in the browser?
<font color="green">What do I load to have the SUnit buttons in the browser?</font>
Load the RBSUnitExtensions parcel from the Visual Works distribution.

@What do I load to have the tabs in my browser?
<font color="green">What do I load to have the tabs in my browser?</font>
Load the RB_Tabs parcel from the Visual Works distribution.

@How do I open an SUnit TestRunner?
<font color="green">How do I open an SUnit TestRunner?</font>
Evaluate <tt>TestRunner open</tt> in a workspace.

@How do I drag and drop a class or namespace definition from one package to another?
<font color="green">How do I drag and drop a class or namespace definition from one package to another?</font>
Make sure the item is <I>unselected</I> before trying to drag and drop it(!).

@How can you get the browser to show all methods when no protocol is selected?
<font color="green">How can you get the browser to show all methods when no protocol is selected?</font>
Open
  System>Settings
and check
  Browser>Show all methods

@How do I interrupt a process?
<font color="green">How do I interrupt a process?</font>
On the Mac, use <I>control</I>Y.

@How do I modify the order in which packages belonging to a bundle are loaded?
<font color="green">How do I modify the order in which packages belonging to a bundle are loaded?</font>
Right-click on the bundle, and select <I>edit bundle specification</I>.