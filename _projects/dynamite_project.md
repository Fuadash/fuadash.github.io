---
layout: page
title: Dynamite @ Softwire
description: Internal project for Softwire where I designed and implemented the Java backend
img: assets/img/dynamite/dynamite3.png
importance: 2
category: work
---

Technologies: React, Java, Spring, TypesScript, Node, HTML, CSS, SQL, AWS

Hosted over at <a href="https://dynamite.softwire.com/">https://dynamite.softwire.com/</a> with the js backend over here <a href="https://github.com/Softwire/DynamiteJS">https://github.com/Softwire/DynamiteJS</a> (don't ask me what happened to the commit history).

I wish I had the Java codebase to show off for this one since it's definitely a lot more impressive than the frontend work of a bunch of new hires without a designer.

Alas, I worked on both the js and the Java backends for this project. A brief rundown of how it works if you don't want to look at the website is: User writes a bot using the provided interface, they can upload the bot, then have it play an abridged version of rock paper scissors against other bots in a couple of different formats. Softwire uses this as part of their onboarding for new hires these days so it ended up being quite a useful project.

If you have knowledge of Java you probably figure that this made heavy use of the reflection API, it was somewhat of a challenge to get it working the first time around but I managed to figure it out. The application is also definitely full of security flaws due to running user generated code which we can't really sanitize but these things just happen really.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/dynamite/dynamite1.png" title="dynamite website image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/dynamite/dynamite2.png" title="dynamite website image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    A crumb of entirely unimpressive frontend design.
</div>
<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/dynamite/dynamite3.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    You will be surprised to hear that we did have a frontend framework but that did not save the frontend design.
</div>
