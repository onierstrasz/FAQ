# Ruby FAQ

Q How do you implement multiple constructors for one class?
A You could explicitly type-check the arguments to initialize.
  A better approach would be to make initialize a private method
  to set all the instance variables. Then implement various
  factory methods at the class level (as you would in Smalltalk).

Q How does Test::Unit determine whether there is a "main program"?
A It doesn't.  You can set Test::Unit.run=true to pretend that
  the tests have already been run.
