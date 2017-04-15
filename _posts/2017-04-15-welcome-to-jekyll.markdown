---
layout: post
title:  "Running and Negating Cucumber tests using Tags"
date:   2016-03-24 12:15:10 +0530
categories: cucumber integration_tests
---
Instead of running the entire test suite Cucumber gives us the option to run only a particular set of tests using Tags.
Example: `cucumber --tags @unit`

If more than one tag should be executed then a comma separated list of values will do the trick. Example: `cucumber --tags @unit,@integration`.

But I was tasked to NOT to run a set of tests which have the specified tag, say *donotrun* (Because those tests should run separately).
Cucumber is giving an option to do that as well. We just have to use `cucumber --tags ~@donotrun`

Wait, what if I don’t want to run tests from more than one tag. If you try something like: `cucumber --tags ~@donotrun,~@neverrun` then you will end up running all the tests. Because it becomes something like `(cucumber --tags ~@donotrun) || (cucumber --tags ~@neverrun)`.

Solution:
For this cucumber lets us using –tags option again.
{% highlight shell %}
cucumber --tags ~@donotrun --tags ~@neverrun
{% endhighlight %}

<!-- Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk]. -->

<!-- [jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
 -->