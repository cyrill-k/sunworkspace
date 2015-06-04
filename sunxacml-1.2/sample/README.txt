
Overview and Introduction To The Samples
---

The samples provided in this package are intended as an introduction to
both the XACML standard and the APIs in this project. Together they
act as examples of how to perform some common tasks, though they do not
cover all the features of either XACML or the APIs. These samples are
complimentary to the Programmer's Guide and the Configuration Guide, so
you should consult both (and the JavaDocs) for answers to your
questions. If you're still stumped, the discission list

  sunxacml-discuss@lists.sourceforge.net

is a good place to try asking questions. You can also try looking at the
source code for the conformance tests, since it exercises a number of
the SunXACML interfaces and shows how to do a number of common tasks.

Note that to run these examples you'll need version 1.4.0 or later of
the Java Runtime Environment. You shouldn't need any other tools or
libraries.

In a nutshell, here is what you'll find in this directory:

  config/     Contains several example run-time configurations. Look in
              that directory for a README with more details on the
              individual files.

  policy/     Contains example XACML policies to get you started. These
              show some of the more commonly used language
              features. Note that none of these have overlapping
              Targets, so they can all be loaded into the same PDP at
              the same time, and the PDP will be able to choose the
              right policy for any given request. Each file contains a
              brief description of the policy's functionality.

  request/    Contains example XACML requests used to query a PDP for an
              authorization decision. Each request has a corresponding
              policy in the policy/ directory. These requests should all
              result in a response of Permit, though some of the
              policies are designed to return different results if you
              change the requests, so if you're curious about how XACML
              works, you should try playing with these files.

  src/        Contains examples of how to use the APIs, as well as some
              generally useful routines. The lib/ directory contains a
              jar file with built versions of this code. Of particular
              importance is the SimplePDP class, which provides a way to
              play with all of the XACML examples. For more information
              about this application and how to run it, look in the
              README-SimplePDP.txt file and at the comments in the
              SimplePDP source file.

              In addition to the SimplePDP application, there are two
              example builder classes that can be invoked directly (and
              are included in the samples.jar file). They let you
              programatically build a simple Request or Policy. Again,
              look at the source files for details about how they work.

As explained above, the requests and policies are paired up to make it a
little clearer how XACML works. Here are some general descriptions of
how the samples relate to each other. All of the XACML examples can be
run by using the SimplePDP program.

  - The request file "generated.xml" and the policy file "generated.xml"
    work together. They show some basic XACML functionality. The source
    files "SampleRequestBuilder.java" and "SamplePolicyBuilder.java" are
    used, respectively, to programatically generate the request and the
    policy file. This shows you how these APIs are used, and what the
    output looks like.

  - The request file "resource-content.xml" and the policy file
    "selector.xml" work together. They show how to use
    AttributeSelectors, and use the example of including resource
    content in the request for determining access. This is a common
    requirement in XML access control systems.

  - The request file "door-access.xml" and the policy file
    "time-range.xml" work together. They show a slightly more complex
    policy scenario, and they use the time-in-range function (explained
    in more detail in the Programmer's Guide). 

  - The request file "sensitive.xml" and the policy file
    "obligation.xml" work together. They show how Obligations work, and
    use the scenario of logging all access requests.

Note that the requests are intentionally designed to be similar, so you
can see how you might operate differently over similar inputs. These
examples are supposed to be fairly simple, so you can use them as a way
to start creating new scenarios to better understand XACML or to meet
your own needs. A good way to get familiar with XACML is to try making
small changes in the requests or policies, and see how the reponses
change. These samples have been designed to make this pretty easy.

In addition to the SimplePDP program and the classes that show how to
generate Requests and Policies, the src/ directory contains a few other
classes:

  - The "SampleAttrFinderModule.java" file shows how to build a new
    attribute finder, which lets the PDP retrieve attribute values
    during policy evaluation. This example shows how a finder can use
    attribute values available in the evaluation context to find other
    values. Note that this is not a runnable example, but it provides
    most of the code you need to support this kind of application.

  - The "SamplePolicyFinderModule.java" file shows how to build a new
    policy finder, which is used by the PDP to find policies for a given
    request or policy reference. This example shows how to handle
    references, and discusses the possibility of dynamically generating
    PolicySets to handle multiple applicable policies. Note that this is
    not a runnable example, but it provides most of the code you need to
    support this kind of application.

  - The "LDAPPolicyFinderModule.java" file shows the starting point for
    building a new policy finder that pulls policies from an LDAP service.
    Like the other sample modules, this class is not runable as-is, but
    provides copious comments to get you started.

  - The "TimeInRangeFunction.java" file provides an implementation of
    this almost-standard function. The Programmer's Guide discusses this
    function, and the reasons why it's useful, in more detail.

That's it. Hopefully these samples will be helpful in getting you
started, but as always feel free to send mail to the discussion lists or
to the project maintainers if you have more questions.
