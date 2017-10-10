---
layout: "post"
title:  "The Exhausting-All-Other-Options Blog"
---

<html lang="en">
<head>
	<meta charset="utf-8" />
	<meta content="width=device-width, initial-scale=1" name="viewport" /><!-- The above 3 meta tags *must* come first in the head; any other head content must come *after* these tags -->
	<meta content="Mental Wanderer's Mental Wanderings" name="description" />
	<meta content="Cory D. Burt" name="author" />
	<meta content="IE=edge" http-equiv="X-UA-Compatible" />
	<link href="/assets/images/favicon.ico" rel="icon" />
	<title>Mental Wanderings</title>
	<!-- Bootstrap core CSS -->
	<link href="/assets/css/bootstrap.min.css" rel="stylesheet" /><!-- Font Awesomeness -->
	<link href="/assets/css/font-awesome.css" rel="stylesheet" /><!-- Local core CSS -->
	<link href="/assets/css/core.css" rel="stylesheet" />
	<link href="/assets/css/font-families.css" rel="stylesheet" />
    <link href="/assets/css/blog.css" rel="stylesheet" /><!-- Custom styles for this template -->
    <!-- HTML5 shim and Respond.js for IE8 support of HTML5 elements and media queries --><!--[if lt IE 9]>
      <script src="https://oss.maxcdn.com/html5shiv/3.7.2/html5shiv.min.js"></script>
      <script src="https://oss.maxcdn.com/respond/1.4.2/respond.min.js"></script>
    <![endif]--><!--- Hosted versions of the dygraphs, jQuery, and AngularJS libraries...
    <script src="https://cdnjs.cloudflare.com/ajax/libs/dygraph/1.1.1/dygraph-combined.js"></script>
    -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.3/jquery.min.js"></script>
    <script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.3.14/angular.min.js"></script>
</head>

<body>
    <div class="blog-masthead">
        <div class="container">
            <nav class="blog-nav"><a class="blog-nav-item active" href="/">&nbsp; Home</a> <a class="blog-nav-item" href="/proj/bootstrap-blog/">Top &#39;O The Heap</a></nav>
        </div>
    </div>

    <div class="container">
        <div class="blog-header">
            <h1 class="blog-title yardsale">Mental Wanderings</h1>

            <p class="lead blog-description jester">The official &quot;Exhausting-All-Other-Resources&quot; blog</p>
        </div>

        <div class="row">
            <div class="col-sm-8 blog-main">
                <div class="blog-post">
                    <h2 class="blog-post-title">What is a Blog?</h2>
                    <p class="blog-post-meta">by <a href="/docs/Cory_Burt_Resume_Current.pdf">Cory</a></p>
                    <p>The word &quot;blog&quot; is a truncation of &quot;weblog,&quot; which is, itself, a compound lexeme comprised of a nickname and a malaprop working under duress.&nbsp; <i>Webs</i>, strictly speaking, are collections of related elements whose organization breaks down when individual elements, or their connection points, are broken.&nbsp; The so-called <i>&quot;World-Wide Web&quot;</i> &ndash; the &quot;web&quot; in &quot;weblog&quot; &ndash; scarcely qualifies.&nbsp; It is, in fact, nothing more than a handful of precious gems scattered around a vast wasteland of unrelated digital peddlers &ndash; sometimes contradictory, poisonous, avaricious, and occasionally defiant of all reason &ndash; dispersed through &quot;clouds, caches, and data centers,&quot; but all found, ultimately, spinning on the hard-drives of &quot;webservers.&quot;</p>
                    <p>It is these servers, sitting like roadside souvenir stands on the shoulder of the information superhighway, that constitute the real infrastructure of this global strip-mall.</p>
                    <p>The word <i>log</i> &ndash; the &quot;log&quot; in &quot;weblog&quot; &ndash; has been adopted here simply because more accurate labels have too many letters in them.&nbsp; Odd though it may be, it must be conceded that the term is not entirely inappropriate.&nbsp; Typically, a log is a sequential record of related events.&nbsp; The sun came up; the sun went down.&nbsp; The clock ticked on.&nbsp; Always a record of routine.&nbsp; A log is something that, in a perfect world, would be perfectly ignored.&nbsp; In fact, the only reason to ever read a log is because we do not live in a perfect world, and someone must, eventually, figure out exactly where the train jumped the rails.</p>
                    <p>So, a <i>blog</i> is a personal play-by-play &ndash; lurking on one of those souvenir stands littering the Internet strip-mall &ndash; that allows the world to discern where your ability to reason, common sense, solid values, manners, good taste &ndash; and sometimes the very fabric of your life &ndash; all went spectacularly wrong...</p>
                    <p>Or, not.&nbsp; In which case &ndash; like any true log &ndash; only your significant other, the NSA, and the human resources department where you work, (if you&#39;re lucky enough to still have a job after all the time you waste blogging), will have any reason to read it.</p>
                </div>

                <!-- /.blog-post -->
                <div class="blog-post">
                    <h2 class="blog-post-title">Easy Form Element Positioning</h2>
                    <p class="blog-post-meta">by <a href="#">Cory</a></p>
                    <p>Here is an example of form field positioning &ndash; with a little help from Bootstrap:</p>
                    <div class="example" ng-app="">
                        <dl class="dl-horizontal">
                            <dt><label for="name">Name</label></dt>
                            <dd><input name="name" ng-model="nameval" type="text" /> &nbsp;<span class="small">{{ nameval }}</span></dd>
                            <dt><label for="address">Address</label></dt>
                            <dd><input name="address" ng-model="addressval" type="text" /> &nbsp;<span class="small">{{ addressval }}</span></dd>
                        </dl>
                        <code>&nbsp;&nbsp;&lt;dl class=&quot;dl-horizontal&quot;&gt;<br />
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;dt&gt;&lt;label for=&quot;name&quot;&gt;Name&lt;/label&gt;&lt;/dt&gt;<br />
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;dd&gt;&lt;input type=&quot;text&quot; name=&quot;name&quot;&gt;&lt;/dd&gt;<br />
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;dt&gt;&lt;label for=&quot;address&quot;&gt;Address&lt;/label&gt;&lt;/dt&gt;<br />
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&lt;dd&gt;&lt;input type=&quot;text&quot; name=&quot;address&quot;&gt;&lt;/dd&gt;<br />
                        &nbsp;&nbsp;&lt;/dl&gt;</code>
                    </div>
                    <p>There are many ways to style a form. &nbsp;Most websites leave the whole business to a framework or use one of many templating systems to simplify the recurring tasks involved.&nbsp; Frameworks and templating systems represent serious design commitments, however, and generally lock a project into one approach for doing everything.&nbsp; Occasionally, such mechanisms are impractical or unavailable, and it makes more sense to take advantage of the steady advance of HTML and CSS standards to enable a somewhat simpler and more direct approach.</p>
                    <p>Bootstrap provides CSS positioning elements specifically for forms, including vertical (stacked fields and labels), in-line (fields and labels across the page), and horizontal (stacked fields with right-justified labels). &nbsp; Sometimes, the &quot;formality of forms&quot; is not necessary because the fields are not intended to be posted to a server. &nbsp; Using <code>&lt;dl&gt;</code> elements that have been styled with Bootstrap makes it very simple to get sensible positioning without using Bootstrap&#39;s form positioning or resorting to brittle custom styles or old-fashioned HTML tricks.&nbsp; Even better &ndash; because its Bootstrap &ndash; the resulting fields are still as mobile-friendly as a full-on Bootstrap form.</p>
                </div>
                <!-- /.blog-post -->

                <nav>
                <ul class="pager">
                    <li><a href="/proj/bootstrap-blog/page2.html">Next</a></li>
                </ul>
                </nav>
            </div>
            <!-- /.blog-main -->

            <div class="col-sm-3 col-sm-offset-1 blog-sidebar">
                <div class="sidebar-module sidebar-module-inset">
                    <h4>About</h4>
                    <p>This is an example of a simple blog page derived from the Bootstrap example set.&nbsp; Other Javascript libraries are included, such as jQuery (which is required for Bootstrap), the Font-Awesome add-on for Bootstrap, AngularJS, Backbone.js, dynagraphs, and others.&nbsp; This demonstrates inter-compatibility among these libraries and some of the other capabilities they add.&nbsp; It is not, of course, a full-fledged content management system such as Joomla.</p>
                </div>

                <div class="sidebar-module">
                    <h4>Archives</h4>

                    <ol class="list-unstyled">
                        <li><a href="#">Archived Posts Would Be Here</a></li>
                    </ol>
                </div>

                <div class="sidebar-module">
                    <h4>Elsewhere</h4>
                        <ol class="list-unstyled">
                            <li><a href="#">This could be a GitHub link</a></li>
                            <li><a href="#">This one would be for Twitter</a></li>
                            <li><a href="#">And, of course, one for Facebook</a></li>
                            <!--
                            <li><a href="/docs/Cory_Burt_Resume_Current.pdf">Someone&#39;s Resume?</a></li>
                            -->
                        </ol>
                </div>
            </div><!-- /.blog-sidebar -->
        </div><!-- /.row -->
    </div><!-- /.container -->

    <!-- Bootstrap core JavaScript
    ================================================== -->
    <!-- Placed at the end of the document so the pages load faster -->
    <script src="/assets/js/bootstrap.min.js"></script>
    <!-- IE10 viewport hack for Surface/desktop Windows 8 bug -->
    <script src="/assets/js/ie10-viewport-bug-workaround.js"></script>
</body>
</html>
