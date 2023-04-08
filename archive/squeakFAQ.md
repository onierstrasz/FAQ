---------------------------------------------------------------------------
Squeak FAQ
---------------------------------------------------------------------------
Moved to http://scg.unibe.ch/wiki/FAQs/pharofaq
---------------------------------------------------------------------------
Q How do I update to the latest image?
A Utilities → updateFromServer
---------------------------------------------------------------------------
Q How do I programmatically run tests of specific categories?
A
| tr |
tr := TestRunner new.
ToolBuilder open: tr.
tr
	categoryAt: (tr categoryList indexOf: 'SCGPier') put: true; "etc"
	selectAllClasses;
	runAll.
---------------------------------------------------------------------------
Q Where do I get the latest Squeak?
A http://ftp.squeak.org/current_development/
---------------------------------------------------------------------------
Q Where is the Squeak "Development Image"?
A http://www.squeaksource.com/ImageForDevelopers/
---------------------------------------------------------------------------
Q How do I browse all references to a given class?
---------------------------------------------------------------------------
Q Which packages should I load from SqueakSource SmaccDevelopment to write parsers?
A Load AST, Refactoring-Core, SmaCC and SmaCCDev
[be sure that SmaCC is up-to-date]
NB: The first two are already in the Squeak/Pharo-dev images
[SmaCC-Development is for 3.8]
---------------------------------------------------------------------------
Q How do I run SmaCC
A Just load SmaCCDev and it will start up -- it will also be loaded into the menu.
---------------------------------------------------------------------------
Q How do I do regexes?
A http://www.squeaksource.com/Regex
---------------------------------------------------------------------------
Q Where are regexes documented?
A VB-Regex RxParser class DOCUMENTATION
---------------------------------------------------------------------------
Q How do I run a headless image with a file argument?
A Can't do it with the MacOSX VM
---------------------------------------------------------------------------
Q How to I search for a class?
A <ALT><click> or <CMD>-F in Browser Category pane
---------------------------------------------------------------------------
Q How do I run SUnit tests?
A TestRunner open
---------------------------------------------------------------------------
Q How do I programmatically start the TestRunner on a specific test class?
A ???
---------------------------------------------------------------------------
Q How do I refactor?
A Load AST then Refactoring Engine from squeaksource.com
http://www.squeaksource.com/AST
http://www.squeaksource.com/RefactoringEngine
Better yet, use the OmniBrowser.
---------------------------------------------------------------------------
- Install latest Universes from SqueakMap
- open Universe Browser
- update list from network
...
---------------------------------------------------------------------------
* NB: This is buggy ...
- Add http://source.wiresong.ca/ob as a Monticello repository
- Load OB-Umbrella
- This will load all the dependent packages and install OB
- NB: there may be problems with loading order -- if the pre-debugger pops up
  just close it and load it again.
- When you try to open the system browser it will prompt you
- Else use the browser menu to select OB as the new browser
- Recompile OB-Morphic OB-Standard and OmniBrowser packages from Monticello
---------------------------------------------------------------------------
Q How do I get tabs in the refactoring browser?
A There are no tabs available :-(
---------------------------------------------------------------------------
Q How do I register the browser that I want to be the default?
A Use the menu in the top left of the Browser window.
---------------------------------------------------------------------------
Q How do I create a SqueakSource project?
A
- go to squeaksource.com
- register yourself as a new member
- register a project (name = category)
- copy the Registration code snippet
- open>Monticello browser
- +Package to add the category
- Select the package
- +Repository>HTTP
- paste and accept the Registration code snippet; enter your password
- Save to save the first version
---------------------------------------------------------------------------
Q How do I load a Squeaksource project?
A
- Find the project in squeaksource
- Copy the Registration code snippet
- open>Monticello browser
- +Repository>HTTP
- paste and accept the Registration code snippet; enter your password
- select the new repository and Open it
- Select and load the latest version
---------------------------------------------------------------------------
Q How do I extend Number with Number>>chf but have Monticello recognize
  it as being part of my Money project?
A Put it in a method-category named *Money
  MC gathers all methods that are in categories named like *package
---------------------------------------------------------------------------
Q How do I find/browse all sends to super?
A SystemNavigation default browseMethodsWithSourceString: 'super'
SystemNavigation default browseAllSelect: [:method | method sendsToSuper ]
---------------------------------------------------------------------------
Q How do I browse all super sends within a hierarchy?
A class := OrderedCollection.
SystemNavigation default
	browseMessageList: (class withAllSubclasses gather: [ :each |
		(each methodDict associations
			select: [ :assoc | assoc value sendsToSuper ])
				collect: [ :assoc | MethodReference class: each selector: assoc key ] ])
	name: 'Supersends of ' , class name , ' and its subclasses'
---------------------------------------------------------------------------
Q How do I convert a collection of characters to a String?
  e.g. 'hello world' asSet ...
A (WriteStream with: String new) nextPutAll: 'hello world' asSet; contents
---------------------------------------------------------------------------
Q How do I select a new default browser?
A See the menu in the top left corner of any browser.
---------------------------------------------------------------------------
Q How do I find out which methods access the Smalltalk dictionary?
A ???
---------------------------------------------------------------------------
Q How do I get the tree view of an AST?
A ???
---------------------------------------------------------------------------
Q How do I find out which are the new methods implemented in a class?
A Example: Integer
[:aClass| aClass methodDict keys select: [:aMethod | (aClass superclass canUnderstand: aMethod) not ]] value: Integer
---------------------------------------------------------------------------
Q How do I tell which methods are abstract?
A [:aClass| aClass methodDict keys select: [:aMethod | (aClass>>aMethod) isAbstract ]] value: Number
---------------------------------------------------------------------------
Q How do I generate a view of the AST of an expression? [cf. 11.12]
A (RBParser parseExpression: '3+4') explore [explore it]
---------------------------------------------------------------------------
Q How do I find all the Traits in the system?
A Smalltalk allTraits
---------------------------------------------------------------------------
Q How do I find which classes use traits?
A Smalltalk allClasses select: [:each | each hasTraitComposition ]
---------------------------------------------------------------------------
Q How to I construct a try/catch block?
A [ ... ] on: Error do: [ ... ]
---------------------------------------------------------------------------
Q Where are method wrappers?
A http://www.squeaksource.com/MethodWrappers
Be sure to load MethodWrappers3.9 for the 3.9 squeak image.
---------------------------------------------------------------------------
Q How do I use method name completion in Squeak?
A <ctrl>-space
---------------------------------------------------------------------------
Q How to save an image as a constant method?
A Just drop an image file onto the Squeak image, inspect it, print 'self form storeString'.
The result will (should) be usable to recreate the image.
For example (self is the ByteString):
(SketchMorph withForm: (Compiler evaluate: self)) openInWorld
---------------------------------------------------------------------------
Q How do I time a block?
A Time millisecondsToRun: aBlock
---------------------------------------------------------------------------
Q How do I introduce a delay?
A (Delay forSeconds: 5) wait.
---------------------------------------------------------------------------
Q How do I refresh a Morph within a method? (i.e., to animate an algorithm)
A Send "self layoutChanged"
??? Does not seem to work ...
---------------------------------------------------------------------------
Q How do I read/write a file?
A (FileDirectory default newFileNamed: 'tmp.txt') nextPutAll: 'stuff'; close.
(FileDirectory default oldFileNamed: 'tmp.txt') contents.
---------------------------------------------------------------------------
Q How do I delete a file?
A FileDirectory default deleteFileNamed: 'testAlpha32.png'
---------------------------------------------------------------------------
Q How do I load an image file?
A (SketchMorph fromFile: 'sq.png') openInWorld
---------------------------------------------------------------------------
Q How do I programmatically load projects from SqueakSource?
A | mc fileToLoad version |
mc := Smalltalk at: #MCHttpRepository ifPresent: [:repoClass | repoClass location: 'www.squeaksource.com/Installer' user: 'squeak' password: 'squeak'].
fileToLoad := mc readableFileNames detect: [ :aFile | aFile beginsWith:'Installer-sd.3' ] ifNone: [ nil ].
version := mc versionFromFileNamed: fileToLoad.
version workingCopy repositoryGroup addRepository: mc.
mc creationTemplate: mc asCreationTemplate.
version load.

NB: Installer provides HL interface to specify load scripts.
---------------------------------------------------------------------------
Q How do I turn off/on smart quotes and auto-completion?
A world menu->open...Preference Browser.  Got to "developer image" category and disable "ecompletionSmartCharacters"
---------------------------------------------------------------------------
Q How do I programmatically set preferences?
A (Preferences dictionaryOfPreferences at: #showDeprecationWarnings) preferenceValue: true.
---------------------------------------------------------------------------
Q How do I find messages sent but not implemented?
A SystemNavigation default browseAllUnimplementedCalls
Also Smalllint: open > code critics on a category will do it.
---------------------------------------------------------------------------
Q How do I prompt the user to select a file or directory?
A FileList2 modalFolderSelector
---------------------------------------------------------------------------
Q How do I run Code critics on a package?
A Start a pharo-dev image with the latest refactoring Browser code in it.
Select your package in the OB class or package browser.
Select open environment > package [opens a package browser]
Select open > Code Critics
[If you directly open code critics, it will analyze the whole smalltalk system!]
---------------------------------------------------------------------------
Q SmaCC pops up an annoying "silence not found in the Sound library" when I click on the tabs -- how do I get it to stop?
A Edit  SampledSound class>>soundNamed: and comment out the "self inform:"
---------------------------------------------------------------------------
Q The Installer complains that the Universe code is not there
A Run: ScriptLoader new installingUniverse
---------------------------------------------------------------------------
Q How do I move all classes and extension methods from one package to another?
A
| pkg |
pkg := PackageInfo named: 'Saphir'.
pkg classes do: [:class | class category: 'Coral' ].
pkg methods collect: [:method |
	method actualClass organization
		classify: method methodSymbol
		under: #'*coral' ]
---------------------------------------------------------------------------
Q How do I programmatically open a workspace?
A 	SHWorkspace new
		contents: 'contents';
		openLabel: 'TASKS'.
---------------------------------------------------------------------------
Q How can I ask if a regex matches any part of string?
A re search: aString
---------------------------------------------------------------------------
Q How do I profile code?
A TimeProfileBrowser spyOn: [ ... ].
---------------------------------------------------------------------------
Q How do I check which methods of my package are not covered by tests?
A Load the ObjectAsMethodWrapper SqueakSource project and run:
category := 'SCGPier'.
w := (ObjectAsOneTimeMethodWrapper installOnClassCategory: category).

tr := TestRunner new.
ToolBuilder open: tr.
[tr
	categoryAt: (tr categoryList indexOf: 'SCGPier') put: true;
	selectAllClasses;
	runAll.]
ensure: [[w do: [:each| each uninstall ]] valueUnpreemptively].

((w select: [:each | each executed not ])
	collect: [:each | each wrappedClass name, '>>', each selector name ]) explore.
---------------------------------------------------------------------------
Q How do I report an error message to the user?
A self inform: ...
---------------------------------------------------------------------------
