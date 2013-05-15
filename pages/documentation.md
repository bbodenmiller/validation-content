<script>{
  "title": "Documentation"
}</script>

== Validate forms like you've never been validating before! ==

'''&quot;But doesn't jQuery make it so very easy to write your own validation plugin?&quot;'''
Sure, but there still are a lot of subtleties that you
have to worry about: You need a standard library of validation methods (think of emails, URLs, credit card numbers). You need to place
error messages in the DOM and show and hide them when appropriate. You want to react to more than just a submit event, like keyup and blur.
You may need different ways to specify validation rules, based on the server-side enviroment you are using on different projects. And after all,
you don't want to reinvent the wheel, do you?

'''&quot;But aren't there already a ton of validation plugins out there?&quot;'''
Right, there are a lot of non-jQuery-based solutions (which you'd avoid since you found jQuery) and some jQuery-based solutions. This particular one you are looking at is one of the oldest jQuery plugins (started in July 2006) and
proved itself in projects all around the world. There is also an [http://bassistance.de/2007/07/04/about-client-side-form-validation-and-frameworks/ article]
discussing how this plugin fits the bill of the should-be validation solution.

Not convinced? Have a look at this example:

== Example ==
{{APIExample|
|height=260
|desc=Validating a comment form.
|code=$(&quot;#commentForm&quot;).validate();
|inhead=&lt;nowiki&gt;&lt;script type=&quot;text/javascript&quot; src=&quot;http://jzaefferer.github.com/jquery-validation/jquery.validate.js&quot;&gt;&lt;/script&gt;
&lt;style type=&quot;text/css&quot;&gt;
* { font-family: Verdana; font-size: 96%; }
label { width: 10em; float: left; }
label.error { float: none; color: red; padding-left: .5em; vertical-align: top; }
p { clear: both; }
.submit { margin-left: 12em; }
em { font-weight: bold; padding-right: 1em; vertical-align: top; }
&lt;/style&gt;&lt;/nowiki&gt;
|html=&lt;nowiki&gt;

 &lt;form class=&quot;cmxform&quot; id=&quot;commentForm&quot; method=&quot;get&quot; action=&quot;&quot;&gt;
 &lt;fieldset&gt;
   &lt;legend&gt;A simple comment form with submit validation and default messages&lt;/legend&gt;
   &lt;p&gt;
     &lt;label for=&quot;cname&quot;&gt;Name&lt;/label&gt;
     &lt;em&gt;*&lt;/em&gt;&lt;input id=&quot;cname&quot; name=&quot;name&quot; size=&quot;25&quot; class=&quot;required&quot; minlength=&quot;2&quot; /&gt;
   &lt;/p&gt;
   &lt;p&gt;
     &lt;label for=&quot;cemail&quot;&gt;E-Mail&lt;/label&gt;
     &lt;em&gt;*&lt;/em&gt;&lt;input id=&quot;cemail&quot; name=&quot;email&quot; size=&quot;25&quot;  class=&quot;required email&quot; /&gt;
   &lt;/p&gt;
   &lt;p&gt;
     &lt;label for=&quot;curl&quot;&gt;URL&lt;/label&gt;
     &lt;em&gt;&amp;nbsp; &lt;/em&gt;&lt;input id=&quot;curl&quot; name=&quot;url&quot; size=&quot;25&quot;  class=&quot;url&quot; value=&quot;&quot; /&gt;
   &lt;/p&gt;
   &lt;p&gt;
     &lt;label for=&quot;ccomment&quot;&gt;Your comment&lt;/label&gt;
     &lt;em&gt;*&lt;/em&gt;&lt;textarea id=&quot;ccomment&quot; name=&quot;comment&quot; cols=&quot;22&quot;  class=&quot;required&quot;&gt;&lt;/textarea&gt;
   &lt;/p&gt;
   &lt;p&gt;
     &lt;input class=&quot;submit&quot; type=&quot;submit&quot; value=&quot;Submit&quot;/&gt;
   &lt;/p&gt;
 &lt;/fieldset&gt;
 &lt;/form&gt;&lt;/nowiki&gt;
}}

==== Isn't that nice and easy? ====
A single line of jQuery to select the form and apply the validation plugin. And a bit of metadata on each
element to specify the validation rules.

Of course that isn't the only way to specify rules. You also don't have to rely on those default messages, but they come in handy when starting
to setup validation for a form.

==== A few things to look for when playing around with the demo ====

* After trying to submit an invalid form, the first invalid element is focused, allowing the user to correct the field. If another invalid field, that wasn't the first one, was focused before submit, that field is focused instead, allowing the user start at the bottom, if he prefers that.
* Before a field is marked as invalid, the validation is lazy: Before submitting the form for the first time, the user can tab through fields without getting annoying messages - he won't get bugged before he had the chance to actually enter a correct value
* Once a field was marked invalid, it is eagerly validated: As soon as the user entered the necessary value, the error message is removed
* If the user enters something in a non-marked field, and tabs/clicks away from it (blur the field), it is validated - obviously the user had the intention to enter something, but failed to enter the correct value

That behaviour can be irritating when clicking through demos of the validation plugin - it is designed for an unobtrusive user experience, annoying the user as little as possible with unnecessary error messages. So when you try out other demos, try to react like one of your users would, and see if the behaviour is better then. If not, please let me know about any ideas you may have for improvements!

== API Documentation ==

You're likely looking for

### [Options for the validate() method](/validate)

If not, read on.

Throughout the documentation, two terms, that you need to know about and their meaning in the context of the validation plugin, are used very often:

* '''method''': A validation method implements the logic to validate an element, like an email method that checks for the right format of an text input's value. A set of standard methods is available, and it is easy to write your own.
* '''rule''': A validation rule associates an element with a validation method, like  &quot;validate input with name &quot;primary-mail&quot; with methods &quot;required&quot; and &quot;email&quot;.

For a start, the validate-method:

=== Plugin methods ===

{{APIList|
{{APIListHeader|Plugin methods}}
{{:Plugins/Validation/validate}}
{{:Plugins/Validation/valid}}
{{:Plugins/Validation/rules}}
{{:Plugins/Validation/removeAttrs}}
}}

=== Custom selectors ===

{{APIList|
{{APIListHeader|Custom selectors}}
{{:Plugins/Validation/blank}}
{{:Plugins/Validation/filled}}
{{:Plugins/Validation/unchecked}}
}}

=== Utilities ===

{{APIList|
{{APIListHeader|String utilities}}
{{:Plugins/Validation/jQuery.validator.format}}
}}

=== Validator ===

The validate method returns a Validator object that has a few public methods that you can use trigger validation programmatically or change the contents of the form. The validator object has more methods, but only those documented here are intended for usage.

{{APIList|
{{APIListHeader|Validator methods}}
{{:Plugins/Validation/Validator/form}}
{{:Plugins/Validation/Validator/element}}
{{:Plugins/Validation/Validator/resetForm}}
{{:Plugins/Validation/Validator/showErrors}}
{{:Plugins/Validation/Validator/numberOfInvalids}}
}}

There are a few static methods on the validator object:

{{APIList|
{{APIListHeader|Validator functions}}
{{:Plugins/Validation/Validator/setDefaults}}
{{:Plugins/Validation/Validator/addMethod}}
{{:Plugins/Validation/Validator/addClassRules}}
}}

=== List of built-in Validation methods ===

A set of standard validation methods is provided:

{{APIList|
{{APIListHeader|Methods}}
{{:Plugins/Validation/Methods/required}}
{{:Plugins/Validation/Methods/remote}}
{{:Plugins/Validation/Methods/minlength}}
{{:Plugins/Validation/Methods/maxlength}}
{{:Plugins/Validation/Methods/rangelength}}
{{:Plugins/Validation/Methods/min}}
{{:Plugins/Validation/Methods/max}}
{{:Plugins/Validation/Methods/range}}
{{:Plugins/Validation/Methods/email}}
{{:Plugins/Validation/Methods/url}}
{{:Plugins/Validation/Methods/date}}
{{:Plugins/Validation/Methods/dateISO}}
{{:Plugins/Validation/Methods/number}}
{{:Plugins/Validation/Methods/digits}}
{{:Plugins/Validation/Methods/creditcard}}
{{:Plugins/Validation/Methods/equalTo}}
}}

Some more methods are provided as addons, currently included in additional-methods.js in the download package.

{{APIList|
{{:Plugins/Validation/Methods/accept}}
{{:Plugins/Validation/CustomMethods/extension}}
{{:Plugins/Validation/CustomMethods/minWords}}
{{:Plugins/Validation/CustomMethods/maxWords}}
{{:Plugins/Validation/CustomMethods/rangeWords}}
{{:Plugins/Validation/CustomMethods/letterswithbasicpunc}}
{{:Plugins/Validation/CustomMethods/alphanumeric}}
{{:Plugins/Validation/CustomMethods/lettersonly}}
{{:Plugins/Validation/CustomMethods/nowhitespace}}
{{:Plugins/Validation/CustomMethods/ziprange}}
{{:Plugins/Validation/CustomMethods/vinUS}}
{{:Plugins/Validation/CustomMethods/dateITA}}
{{:Plugins/Validation/CustomMethods/phoneUS}}
}}

== [[Plugins/Validation/Reference|General Guidelines]] ==

The General Guidelines section provides detailed discussion of the design and ideas behind the plugin, explaining why certains things are as they are. It covers features in more detail then the API documentation, which just briefly explains the various methods and options available.

If you decided to use the validation plugin in your application and want to get it to know better, it is recommended to read those guidelines.

=== Fields with complex names (brackets, dots) ===

One of the most common issues, see the [[Plugins/Validation/Reference#Fields_with_complex_names_.28brackets.2C_dots.29|reference for details]].

=== Too much recursion ===

Another common problem occurs with this code:

 $(&quot;#myform&quot;).validate({
  submitHandler: function(form) {
    // some other code
    // maybe disabling submit button
    // then:
    $(form).submit();
  }
 });

This results in a too-much-recursion error: $(form).submit() triggers another round of validation, resulting in
another call to submitHandler, and voila, recursion. Replace that with
form.submit(), which triggers the native submit event instead and not
the validation.

So the correct code looks slightly different:

 $(&quot;#myform&quot;).validate({
  submitHandler: function(form) {
    form.submit();
  }
 });

== Demos ==

=== [http://jquery.bassistance.de/validate/demo/marketo/ The Marketo sign-up form] ===
==== [http://jquery.bassistance.de/validate/demo/marketo/step2.htm The Marketo sign-up form, step 2] ====
Based on the marketo.com sign-up form. The custom validation was replaced with this plugin. Thanks to Glen Lipka for contributing it!

''Notable features of the demo:''
* Customized message display: No messages displayed for the required method, only for type-errors (like wrong email format); A summary is displayed at the top (&quot;You missed 12 fields. They have been highlighted below.&quot;)
* Remote validation of email field. Try to enter eg. glen@marketo.com
* Integration with masked-input plugin, see Zip and Phone fields and Credit Card Number on step 2
* A custom method for making the billing address on step 2 optional when &quot;Same as Company Address&quot; is checked
* A custom method for checking the password: Checks that the password contains at least one number and one character and that it is at least 6 characters long. If the user blurs the field with an invalid value, the input emptied and gets focus again.

=== [http://jquery.bassistance.de/validate/demo/milk/ The Remember The Milk sign-up form] ===
The sign-up form from rememberthemilk.com (based on an older version). The custom validation was replaced using this plugin. Thanks to RTM for contributing!

''Notable features of the demo:''
* Custom message display, based on the original table layout, using success option to display a checkmark for valid fields
* Remote validation of username, to check if it is already taken (try &quot;Peter&quot;, &quot;asdf&quot; or &quot;George&quot;)

=== [http://jquery.bassistance.de/validate/demo/multipart/ A multipart &quot;buy&amp;sell a house&quot; form] ===
Contributed by Michael Evangelista, showing a multipart form for buying and selling houses.

''Notable features of the demo:''
* Multipart, implemented using the jQuery UI accordion and a custom method to check if an element is on the current page when validated
* Integration with masked-input plugin, see Phone and Zip fields

=== [http://jquery.bassistance.de/validate/demo/captcha/ Using remote validation to help with captchas] ===
Features remote validation for helping the user to fill out captchas, based on example at [http://psyrens.com/captcha/ psyrens.com].

''Notable features of the demo:''
* Remote validation to check if the user entered the correct captcha, without forcing him to submit the form first