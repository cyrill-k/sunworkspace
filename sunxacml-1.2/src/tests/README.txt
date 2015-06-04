
This directory contains a very simple, highly un-optimized set of
classes for running the standard conformance tests against the SunXACML
project. This is being provided by popular demand, but is not ready now
for anyone to extend the code or add new test cases. If you are
interested in transforming this into a real test system capable of
handling new tests, please contact sethp@users.sourceforge.net, who will
be grateful for the help!

To run the tests, you first need a copy of the core SunXACML code (or
a built jar file). You also need the standard XACML conformance tests,
which can be found off the XACML TC's home page at:

  http://www.oasis-open.org/committees/tc_home.php?wg_abbrev=xacml

Next you should look at the settings for sunxacml and confDir in the
build.xml file, and set them as appropriate based on where you have the
SunXACML library and the conformance tests. Finally, you use Ant to
built and run the test code.
