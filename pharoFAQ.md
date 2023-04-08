# Pharo FAQ

See also: http://scg.unibe.ch/wiki/faq/pharo

## Q How to run the Pharo launcher on a Mac?

The Mac does not allow the launcher to run because it can't check for malicious software. You have to disable the check :-(
```
sudo spctl --master-disable
```

https://www.imore.com/how-open-apps-anywhere-macos-catalina-and-mojave

## Q How to launch the Pharo launcher on a Mac?

*Problem:* the launcher won't launch. It just sits there.

*Solution:* change the launcher setting to launch with login shell (query `login` in the settings and uncheck `Launch image from a login shell`)

*manuel 11:39 AM:*
I talked with Christophe, the problem you described did not sound familiar to him, so I guess it is really machine specific. As an entry point, you can spawn spotter in the Pharo Launcher (shift+enter), the search for PhlImage, in the system browser you can now set a breakpoint in #launchWithSettings:. Launching an image should now open the debugger, and you can now inspect the command that is executed. Maybe you can use this to reproduce the error from command line.
I had a quick chat with Christophe regarding the launcher issue. For him it does not have a high priority, there are more pressing things for him to solve currently. But he hinted me at one thing we did not try yet: There already is a setting for the launcher "Use login shell", which is on by default. Could you try disabling that and running your images with a new version of the launcher? I think it should work, as long as there are no external calls to OS processes relying on a login environment, e.g. a specific binary being on the path.

## Q How to set up an Iceberg repo?

*Easiest:* create an empty repo on github or elsewhere, with a “src” subfolder and clone it. Import it into Iceberg and initialize/repair it, specifying that source is in the “src” folder.

*Alternatively:* Add your package `XYZ` to the repo using Iceberg, and also add a `BaselineOfREPO` package with a `BaselineOfREPO` class that subclasses `BaselineOf` and has a `baseline:` method that specifies eg:
```
	baseline: spec
		<baseline>
		spec
			for: #common
			do: [ spec package: #'XYZ' ]
```

## Q Why won't Iceberg let me push to github?
Try running
```
ssh-add ~/.ssh/id_rsa
```

## Q Why do I get the error `revspec 'master' not found.` ?

Newly created repositories only have a `main` branch. However, the default in Metacello is `master`. 
So, you have to specify the branch explicitly in your url:
```
	Metacello new baseline: 'GtFAQ'; repository: 'github://onierstrasz/GtFAQ:main/src'; load.
```

## Q How to script cloning/loading of a git repo?
```
	| path |
	path := '/Users/oscar/Documents/Projects/GTExperiment-Brewery'.
	(IceRepositoryCreator new
		repository: nil;
		location: path asFileReference;
		createRepository) register
```

## Q Why can't I clone, pull or push private repos from Iceberg?

For some reason ssh is not working correctly. If all else fails, try to change the Iceberg settings to `Use custom SSH keys`. Then verify that you can clone, commit and push.

AS says: *Apparently in MacOS starting from 10.12.2 Apple changed something, so if you want a global proper solution then add the following to ~/.ssh/config :*
```
	Host *
	   AddKeysToAgent yes
	   UseKeychain yes
```
https://www.ssh.com/academy/ssh/config#commonly-used-configuration-options


## Q How do I find a method containing a particular string?
```
SystemNavigation new allMethodsWithSourceString: 'Clone from' matchCase: false
```

## Q How do I overcome the problem : “Pharo6.1-64.app” is damaged and can’t be opened. You should move it to the Trash.

This is a Gatekeeper issue. Just run:
```	
sudo xattr -rd com.apple.quarantine <LockedApp.app>
```

## Q How do I download a file from a URL?
```
'http://scg.unibe.ch/download/scgbib/scg.bib' asZnUrl retrieveContents
```

## Q What is the keyboard shortcut to activate Spotter in Pharo 4?
`<SHIFT><ENTER>`

## Q How to debug PetitParser?
Navigate to the parse: stack frame and inspect the result ivar -- this will give you a dedicated debug view

## Q How do I use GitFileTree?

- Create *and initialize* a git repo
- Load GitFileTree (with the Configuration Browser)
- Add a Remote git repo with Monticello *and give it a name*: `name: '...'`
- Add your package to the repo
- Save; push

## Q How do I find a class in the System Browser?
```
<CMD>FC
```

## Q How do I load a file from the file system?
```
(FileStream oldFileNamed: '/Users/...') contents
```
This should work, but is broken in Pharo (works in Gt):
```  
filePath asFileReference contents
```  
This is the workaround:
```
(FileLocator imageDirectory asFileReference / 'Calls.txt') contents
```

* How do I browse for a file from the file system?

  (UITheme builder fileOpen: 'Import file') contents

* How do I run an expression with a progress bar?

* How do I open a FileReference to a directory?

    FileReference fileSystem: FileSystem disk path: '/Users/oscar/Dropbox/Mongo/import/sira-members' asPath.

---
