
This package includes a demo application called SimplePDP which lets you try
running policies to see how they evaluate given different requets. It's also
a useful piece of example code to understand how you would start buildling
your own PDP. Included in this sample package are several requests and
policies to get you started.

To run the SimplePDP application you need to have, in your CLASSPATH, one of
the two sunxacml jar files and the samples.jar file. All these files are
available in the lib directory. Once you have this setup, you can invoke the
SimplePDP application in one of two ways.


Running with built-in configuration
---

As in previous versions of this project, you can run a basic version of the
SimplePDP application that is pre-configured with default factories and 
some finder modules. In order to run this version of SimplePDP, you invoke
the class with a request and one or more policies:

  java SimplePDP <request> <policy> [policies]

The PDP will try to load all the policies, load the request, and then will
pick the right policy and perfrom the evaluation. Cool, huh? If you want to
use the example files provided in this project, you can just do something
like:

  java SimplePDP request/sensitive.xml policy/*.xml

Once you get comfortable with this, try looking at the requests and policies,
and tweak the values. Then, see if you're getting the results you expect.
This is a great way to learn XACML, or to see if you understand how a certain
feature works.


Running with run-time configuration
---

New in the 1.2 release, there is a run-time configuration feature that lets
you define the contents of your PDP (factories and configuration modules) from
a configuration file. To run SimplePDP in this mode, invoke it like:

  java -Dcom.sun.xacml.PDPConfigFile=<config> SimplePDP -config <request>

In this mode, the PDP will pull its configuration from the given config file,
load the request, and then evaluate in the same manner. Note that in this
method you don't supply any policies. That's because they're specified in
the configuration file. There are a couple examples in the config directory,
but if you want to emulate the non-config version of SimplePDP, you should
use the sample2.xml configuration:

  java -Dcom.sun.xacml.PDPConfigFile=config/sample2.xml SimplePDP -config request/sensitive.xml

This does the same thing as the non-config version. For more on how the config
system works, look in the doc directory for the run-time configuration guide.


Trouble-shooting
---

If you're having trouble getting this to work check that you're in the sample
directory (or that you've changed the above paths appropriately), and that
your CLASSPATH correctly includes the two jar files. Also, make sure that
you're using version 1.4.0 or later of the Java Runtime Environment. If all
else fails, send mail to the SunXACML discussion list:

  sunxacml-discuss@lists.sourceforge.net

Hopefully someone there will be able to help you out.

One thing to note. When you run these examples, you'll probably see some number
of log messages like "INFO: Failed to resolve any values for...". Yes, this is
normal. These messages appear because some of the requests/policies include
an issuer in the resource-id attribute, and others don't. These are treated as
different values in XACML. When the PDP tries to find a matching policy, it
looks at all available policies, and some of them (the ones that don't apply
to the request you're using) will look for (and fail to find) the version of
the resource-id they want.

If you don't want to see these messages, then configure the logging system to
stop displaying messages at the INFO level. For an example of how this works,
look in the src directory at the tests code, which includes a log config
file to do this kind of thing.

