# SVN FAQ

Q How do I install a subversion client?
A You can grab an installer for Mac OSX from here: http://www.codingmonkeys.de/mbo/

Q How do I authenticate myself to svn?
A You should add a user and password for yourself using htpasswd to the password file (in ~scg/.svn/). Remote users should use htpasswd -n to generate an entry and ask an scg member to add this to the authorization file. You may need to add a new user to the scg group in the authorization file (also in ~scg/.svn/). Non-scg users should be granted access individually to specific directories.  (See the examples, or read *http://svnbook.red-bean.com/en/1.2/svn.serverconfig.httpd.html#svn.serverconfig.httpd.authz*)

Q How do I create a new SCG svn directory?
A svn import https://www.iam.unibe.ch/scg/svn_repos/MyPath

Q How do I checkout an SCG svn directory?
A svn co https://www.iam.unibe.ch/scg/svn_repos/MyPath

Q Can I set an environment variable to tell svn which repository to use?
A No. But you only need to specify the repository when importing a new directory or checking out an existing one. You might want to define an environment variable as follows:
setenv sv https://www.iam.unibe.ch/scg/svn_repos
Then you can simply checkout as follows:
svn co $sv/scgbib

Q How does svn differ from cvs?
A See: http://svnbook.red-bean.com/nightly/en/svn.forcvs.html

Q How can I convert my cvs project to svn?
A Try cvs2svn (on asterix).  There is a script in ~scg/Cmd/scgcvs2svn
that will automate the process.

Q How do I resolve conflicts with svn
A As before, but now you must use "svn resolved" to announce that you have resolved the conflicts. See:
http://svnbook.red-bean.com/nightly/en/svn.ref.svn.c.resolved.html

Q How can I enable keyword expansion in svn documents?
A Use: svn propset svn:keywords "Date Author Id Log" <file>

Q Subversion keeps printing <code>Authentication realm: ...</code> when I try to commit my changes, and prompts me again for my login and password.  What does this mean and how do I fix it?
A You don't have permission to modify that directory. Perhaps you need to update the svn-access file on asterix.  See instructions in ~scg/.svn/

Q Where is svn on asterix?
A It will appear in your path if you do "module load subversion.

Q How can I view my subversion directories through the web?
A *https://www.iam.unibe.ch/scg/svn_repos* will prompt you for your svn login and password

Q How can I make a directory publicly visible?
A Grant read access to everybody by adding a line "* = r" for your directory in the authorization file (in ~scg/.svn/)

Q What is typical interaction for the scg repository?
A

```
# Create a wonderful project
mkdir MyProject
cd MyProject
# Import it somewhere in the svn directory hierarchy
svn import https://www.iam.unibe.ch/scg/svn_repos/mystuff/MyProject -m "svn demo"
# List the contents of a directory
svn list https://www.iam.unibe.ch/scg/svn_repos/mystuff
# Get rid of the old copy
cd ..
rm -rf MyProject
# Check out a copy
svn co https://www.iam.unibe.ch/scg/svn_repos/mystuff/MyProject
# Add some files
cd Myproject
who > stuff
svn add stuff
# Check the status of the files
svn status
# Commit changes
svn commit -m "This is important stuff"
# Delete a whole directory
svn delete https://www.iam.unibe.ch/scg/svn_repos/mystuff -m "end of demo"
```
