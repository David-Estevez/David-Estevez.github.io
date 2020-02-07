---
title: "David Estevez"
keywords: David Estevez DEF homepage
hide_tags: true
hide_sidebar: true
toc: false
permalink: index.html
---

<div class="row">
  <div class="col-md-3 col-sm-3 text-center">
    {% include image.html file="me.jpg" alt="Picture of myself" rounded=true %}
  </div>
  <div class="col-md-9 col-sm-9 about-me">
    <p>Ph.D candidate in Robotics and Machine Learning at University Carlos III of Madrid, researching about garment perception and manipulation applied to robotics (i.e. teaching a robot how to do the laundry). My  interests go from robotics and machine learning applied to robots, to building elecronics and other contraptions in my spare time.</p>
  </div>
  <div class="text-center">
  {% for element in site.social %}
      <a class="no_icon" href="{{element.url}}">
      <span class="fa-stack fa-2x">
            <i class="fa fa-circle fa-stack-2x text-primary"></i>
            <i class="fa fa-{{element.title}} fa-stack-1x fa-inverse"></i>
      </span>
      </a>
  {% endfor %}
  </div>
</div>

<div class="row">
    <div class="col-lg-12 page-header"></div>
    <div class="col-lg-12">
        <div id="myTabContent" class="tab-content">
            <div class="tab-pane fade active in" id="service-blog">
                <div class="row">
                  <div class="col-lg-12">
                      <h2 class="page-header no-anchor recent-header">Recent Posts</h2>
                  </div>
                  {% for post in site.posts limit:3 %}
                  <div class="col-md-4">
                      <div class="panel panel-default text-center">
                          <div class="panel-heading">
                              {% if post.image.feature %}
                                <img class="card-img-top" src="img/blog/{{post.image.feature}}" alt="Post featured image">
                              {% else %}
                              <span class="fa-stack fa-5x">
                                    <i class="fa fa-circle fa-stack-2x text-primary"></i>
                                    <i class="fa fa-edit fa-stack-1x fa-inverse"></i>
                              </span>
                              {% endif %}
                          </div>
                          <div class="panel-body">
                              <h4 class="no-anchor">{{ post.title }}</h4>
                              <p>{% if page.summary %} {{ page.summary | strip_html | strip_newlines | truncate: 40 }} {% else %} {{ post.content | truncatewords: 36 | strip_html }} {% endif %}</p>
                              <a href="{{ post.url | remove: "/" }}" class="btn btn-primary">Read Post</a>
                          </div>
                      </div>
                  </div>
                  {% endfor %}
            </div>
        </div>
    </div>
</div>

<div class="row">
<div class="col-lg-12 page-header"></div>
<div class="container">
  <div class="col-lg-12">
    <a href="/news.html" class="btn btn-primary btn-block githubEditButton" role="button"><i class="fa fa-edit fa-lg"></i> <b>Blog Posts (Spanish Only)</b></a>
  </div>
</div>
<div class="container">
  <div class="col-lg-12">
    <a href="/research.html" class="btn btn-primary btn-block githubEditButton" role="button"><i class="fa fa-search fa-lg"></i><b>Research</b></a>
  </div>
</div>
<div class="container">
  <div class="col-lg-12">
    <a href="/projects.html" class="btn btn-primary btn-block githubEditButton" role="button"><i class="fa fa-code fa-lg"></i><b>Projects</b></a>
  </div>
  <div class="col-lg-12">
    <a href="/tutorials.html" class="btn btn-primary btn-block githubEditButton" role="button"><i class="fa fa-map-signs fa-lg"></i><b>Tutorials</b></a>
  </div>
</div>
</div>


