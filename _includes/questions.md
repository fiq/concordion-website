{% assign spec_type=page.spec_type %}
{% if spec_type == 'html' %}
{% assign html=true %}
{% assign md=false  %}
{% assign spec_type_desc = 'HTML' %}
{% assign ext='html' %}
{% elsif spec_type == 'markdown' %}
{% assign html=false %}
{% assign md=true    %}
{% assign spec_type_desc = 'Markdown' %}
{% assign ext='md'    %}
{% endif %}

{% assign fixture_language=page.fixture_language %}
{% if fixture_language == 'java' %}
{% assign java=true %}
{% assign csharp=false  %}
{% assign fixture_language_desc = 'Java' %}
{% assign supports_full_ognl = true %}
{% elsif fixture_language == 'csharp' %}
{% assign java=false %}
{% assign csharp=true %}
{% assign fixture_language_desc = 'C#' %}
{% assign supports_full_ognl = false %}
{% endif %}

_This page shows the FAQ for __{{ fixture_language_desc }}__._  Click the toggle buttons above to choose other options.

<a name="whoDevelopedIt"> </a>

### Who developed Concordion{% if csharp %}.NET{% endif %}?
{% if java %}

Concordion was originally developed by David Peterson. The idea was sparked by conversations with testers and developers, in particular Nat Pryce and Steve Freeman while working at Easynet (BSkyB) in 2006.

In 2013, Nigel Charman took over as project lead, having developed the Concordion extensions mechanism. 

Version 2.0 of Concordion was released in 2016 by a team of contributors.

{% elsif csharp %}

Concordion.NET was originally ported from the Java version by Jeffrey Cameron.

In 2013, ShaKaRee took over as project lead, and updated the code base. In 2016, ShaKaRee brought the code to parity with the Java version by cross-compiling it using IKVM.NET and performance tuning it to be faster than the previous natively compiled version.

{% endif %}

Concordion has been ported and further extended by several other developers.

See the <a class="modal-trigger" href="#modal-contributors">Concordion team</a>.

<a name="licensing"> </a>

### How is Concordion licensed?

Concordion is licensed under the Apache License, v2.0.

See <a href="https://github.com/concordion/concordion{% if csharp %}.net{% endif %}/blob/master/LICENSE.{% if csharp %}md{% elsif java %}txt{% endif %}">here</a> for the license text.

<a name="mailingList"> </a>

### Is there a mailing list?
Yes, on Google Groups. [Join here](http://groups.google.com/d/forum/concordion{% if csharp %}-for-net{% endif %}).

We also have a [developer list](http://groups.google.com/d/forum/concordion-dev) for discussing development of Concordion core and extension code. 

<a name="twitter"> </a>

### Is there a twitter account?

Yes!

<a class="twitter-timeline" height="250px" data-chrome="nofooter" href="https://twitter.com/concordion" data-widget-id="526560172584341504">Tweets by @concordion</a>
<script>!function(d,s,id){var js,fjs=d.getElementsByTagName(s)[0],p=/^http:/.test(d.location)?'http':'https';if(!d.getElementById(id)){js=d.createElement(s);js.id=id;js.src=p+"://platform.twitter.com/widgets.js";fjs.parentNode.insertBefore(js,fjs);}}(document,"script","twitter-wjs");</script>


<a name="issueList"> </a>

### How do I report defects or submit enhancement requests?

In Concordion{% if csharp %}.NET{% endif %}'s [Issues List](https://github.com/concordion/concordion{% if csharp %}.net{% endif %}/issues).


<a name="sourceCode"> </a>

### Where is the source code repository?

It is hosted on GitHub: [Main Project Page](https://github.com/concordion/concordion{% if csharp %}.net{% endif %}), [all Concordion projects](https://github.com/concordion). The current development version (potentially unstable) can be cloned as follows:

~~~command
git clone https://github.com/concordion/concordion{% if csharp %}.net{% endif %}.git
~~~

<a name="collaborate"> </a>

### How do I collaborate with development of Concordion?

Firstly, you should [create an issue](#issueList) for your enhancement request.

Concordion uses a "Fork &amp; Pull" model for collaborative development. If you have changes that you would like us to consider for introduction to Concordion, you will need to [fork](https://help.github.com/articles/fork-a-repo) the repository, commit and push your changes to your forked project, and send us a [pull request](https://help.github.com/articles/using-pull-requests) referencing the URL of the issue that you created.

Please note that, in order to keep Concordion clean and minimal, we consider all enhancement requests carefully. Should your enhancement not be appropriate for Concordion core, you may wish to package it as a Concordion [extension]({{site.baseurl}}/coding/{{ page.fixture_language }}/{{ page.spec_type }}#creating-an-extension). 

{% if java %}

See README-DEVELOPERS.txt in the concordion repository for the development standards.

{% endif %}

<a name="comparisonWithSelenium"> </a>

### How does Concordion differ from Selenium?

[Selenium](http://docs.seleniumhq.org) is a test scripting tool for driving web browsers.
Concordion is a specification tool and hides scripting activity inside Java fixture code. For tests that exercise the browser, we recommend  [Selenium WebDriver](http://docs.seleniumhq.org/projects/webdriver/) with Concordion.

{% if java %}

The [screenshot extension demo](https://github.com/concordion/concordion-screenshot-extension-demo) project demonstrates Concordion working with Selenium WebDriver.

{% endif %}

{% if supports_full_ognl %}
<a name="complexExpressions"> </a>

### How do I use complex expressions in my Concordion specifications?

In order to [keep your specifications simple]({{site.baseurl}}/technique/{{ page.fixture_language }}/{{ page.spec_type }}#keepSpecsSimple) and maintainable, Concordion deliberately restricts the expression format that is allowed when instrumenting specifications. Complexity should be moved into the fixture code, and then [evolved into a DSL]({{site.baseurl}}/technique/{{ page.fixture_language }}/{{ page.spec_type }}#evolveDSL), where it is easier to maintain. The idea is to have the fixture do all the work of fetching and munging the data and then return exactly the data that the spec needs, which helps to decouple the spec from the implementation.

However, if you really want to remove this restriction you can apply the annotation @FullOGNL to your fixture class. This would allow you to do things like [pass property values of Java beans into methods](http://stackoverflow.com/questions/23658633/use-result-object-of-first-concordion-call-as-arg-in-secound-concordion-call), or [use constant values in concordion:execute commands](http://stackoverflow.com/questions/19681470/sending-a-constant-parameter-to-concoridion-execute-call). 

{% endif %}

<a name="ownDogFood"> </a>

### Does Concordion itself have active specifications?

Yes, see the [Concordion{% if csharp %}.NET{% endif %} specifications]({% if java %}http://concordion.github.io/concordion/latest/spec/Concordion.html{% elsif csharp %}http://concordion.org/dotnet/Concordion/Concordion.html{% endif %}).