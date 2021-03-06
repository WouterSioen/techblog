---
layout: post
status: publish
published: true
title: Move your mouse pointer with Java
author:
  display_name: Joe Wright
  login: joejag
  email: joe@joejag.com
  url: ''
author_login: joejag
author_email: joe@joejag.com
wordpress_id: 986
wordpress_url: http://code.joejag.com/?p=986
date: '2013-06-07 10:36:12 +0100'
date_gmt: '2013-06-07 09:36:12 +0100'
categories:
- Uncategorized
tags: []
comments:
- id: 168
  author: Dan
  author_email: news@dannyclark.com
  author_url: ''
  date: '2013-06-10 21:06:55 +0100'
  date_gmt: '2013-06-10 20:06:55 +0100'
  content: 'Nice. We solved the same problem with: http:&#47;&#47;www.zhornsoftware.co.uk&#47;caffeine&#47;.
    Added to the startup menu and now our status screen never times out. Believe it
    or not, the desktop support guy suggested it.'
- id: 169
  author: Forrest Haller
  author_email: forrest.haller@yahoo.com
  author_url: ''
  date: '2013-12-14 23:40:16 +0000'
  date_gmt: '2013-12-14 22:40:16 +0000'
  content: Hey do you think you could use robot to make the directional keys move
    the mouse around? Im trying to make an application that will allow me to use my
    keyboard as a mouse.
---
<p>At work we have a big TV screen with a build status being displayed. The desktop support team had a large lead time on changing the settings to stop it locking the machine every 5 minutes. This was the temporary workaround.</p>
<p>The <strong>java.awt.Robot</strong> has a few other interesting methods like taking screenshots, getting the colour under your cursor and clicking the mouse. </p>
<p>This code has no dependencies.</p>

{% highlight java %}
import java.awt.Robot;
import java.util.Random;

public class MouseMover {
    public static final int FIVE_SECONDS = 5000;
    public static final int MAX_Y = 400;
    public static final int MAX_X = 400;

    public static void main(String... args) throws Exception {
        Robot robot = new Robot();
        Random random = new Random();
        while (true) {
            robot.mouseMove(random.nextInt(MAX_X), random.nextInt(MAX_Y));
            Thread.sleep(FIVE_SECONDS);
        }
    }
}
{% endhighlight %}

I've compiled a version using Java7 which you can <a href="/assets/MouseMover.class">download</a> and use right away.
