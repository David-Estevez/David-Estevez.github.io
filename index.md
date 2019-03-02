---
title: "David Estevez"
keywords: David Estevez DEF homepage
hide_tags: true
hide_sidebar: true
toc: false
permalink: index.html
---

<div class="row">
  <div class="col-md-3 col-sm-3">
    {% include image.html file="me.png" alt="Picture of myself" rounded=true %}
  </div>
  <div class="col-md-9 col-sm-9 about-me">
    <p>Electronics Engineer with a M.Sc in Robotics. I am currently working on my Ph.D at University Carlos III of Madrid, researching about garment perception and manipulation applied to robotics (i.e. teaching a robot how to do the laundry). My research interests are Computer Vision, Robotics, and Mixed Reality applied to robots.</p>
  </div>
  <div class="pull-left">
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

<!-- Service Tabs -->
<div class="row">
    <div class="col-lg-12 page-header">
    </div>
    <div class="col-lg-12">

        <ul id="myTab" class="nav nav-tabs nav-justified">
            <li class="active"><a href="#service-blog" data-toggle="tab"><i class="fa fa-edit"></i> Blog</a>
            </li>
            <li class=""><a href="#service-research" data-toggle="tab"><i class="fa fa-search"></i> Research</a>
            </li>
            <li class=""><a href="#service-projects" data-toggle="tab"><i class="fa fa-code"></i> Projects</a>
            </li>
            <li class=""><a href="#service-tutorials" data-toggle="tab"><i class="fa fa-map-signs"></i> Tutorials</a>
            </li>
        </ul>

        <div id="myTabContent" class="tab-content">
            <div class="tab-pane fade active in" id="service-blog">
                <h4 class="no-anchor">Blog</h4>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quae repudiandae fugiat illo cupiditate excepturi esse officiis consectetur, laudantium qui voluptatem. Ad necessitatibus velit, accusantium expedita debitis impedit rerum totam id. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Natus quibusdam recusandae illum, nesciunt, architecto, saepe facere, voluptas eum incidunt dolores magni itaque autem neque velit in. At quia quaerat asperiores.</p>
                <!-- Service List -->
                <!-- The circle icons use Font Awesome's stacked icon classes. For more information, visit http://fontawesome.io/examples/ -->
                <div class="row">
                  <div class="col-lg-12">
                      <h2 class="page-header no-anchor">Recent Posts</h2>
                  </div>
                  {% for post in site.posts limit:2 %}
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
                              <p>{% if page.summary %} {{ page.summary | strip_html | strip_newlines | truncate: 40 }} {% else %} {{ post.content | truncatewords: 40 | strip_html }} {% endif %}</p>
                              <a href="{{ post.url | remove: "/" }}" class="btn btn-primary">Read Post</a>
                          </div>
                      </div>
                  </div>
                  {% endfor %}
                  <div class="col-md-4">
                      <div class="panel panel-default text-center">
                          <div class="panel-heading">
                              <span class="fa-stack fa-5x">
                                    <i class="fa fa-circle fa-stack-2x text-primary"></i>
                                    <i class="fa fa-edit fa-stack-1x fa-inverse"></i>
                              </span>
                          </div>
                          <div class="panel-body">
                              <h4 class="no-anchor">Latest Posts</h4>
                              <p>Check out the latest posts published on the blog.</p>
                              <a href="news.html" class="btn btn-primary">Check Out!</a>
                          </div>
                      </div>
                  </div>
                </div>
            </div>
            <div class="tab-pane fade" id="service-research">
                <h4 class="no-anchor">Research</h4>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quae repudiandae fugiat illo cupiditate excepturi esse officiis consectetur, laudantium qui voluptatem. Ad necessitatibus velit, accusantium expedita debitis impedit rerum totam id. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Natus quibusdam recusandae illum, nesciunt, architecto, saepe facere, voluptas eum incidunt dolores magni itaque autem neque velit in. At quia quaerat asperiores.</p>
                <!-- Service List -->
                <!-- The circle icons use Font Awesome's stacked icon classes. For more information, visit http://fontawesome.io/examples/ -->
                <div class="row">
                  <div class="col-lg-12">
                      <h2 class="page-header no-anchor">Research Lines</h2>
                  </div>
                  <div class="col-md-4">
                    <div class="panel panel-default text-center">
                        <div class="panel-heading">
                          <img class="card-img-top" src="img/research/garments-thumbnail.png" alt="Garment Perception and Manipulation featured image">
                        </div>
                        <div class="panel-body">
                          <h4 class="media-heading no-anchor">Garment Perception and Manipulation</h4>
                          <p>When robots do laundry.</p>
                          <a href="research.html" class="btn btn-primary">View topic</a>
                        </div>
                    </div>
                  </div>
                  <div class="col-md-4">
                    <div class="panel panel-default text-center">
                        <div class="panel-heading">
                          <img class="card-img-top" src="img/research/modularrobots-thumbnail.png" alt="Modular robots featured image">
                        </div>
                        <div class="panel-body">
                          <h4 class="media-heading no-anchor">Modular Robots</h4>
                          <p>When robots are made of robots.</p>
                          <a href="research.html" class="btn btn-primary">View topic</a>
                        </div>
                    </div>
                  </div>
                  {% comment %} (To be enabled in the future)
                  <div class="col-md-4">
                    <div class="panel panel-default text-center">
                        <div class="panel-heading">
                            <span class="fa-stack fa-5x">
                                  <i class="fa fa-circle fa-stack-2x text-primary"></i>
                                  <i class="fa fa-search fa-stack-1x fa-inverse"></i>
                            </span>
                        </div>
                        <div class="panel-body">
                            <h4 class="no-anchor">Publications</h4>
                            <p>List of all my academic publications.</p>
                            <a href="404.html" class="btn btn-primary">View publications</a>
                        </div>
                    </div>
                  </div>
                  {% endcomment %}
                </div>
            </div>
            <div class="tab-pane fade" id="service-projects">
                <h4 class="no-anchor">Projects</h4>
                <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quae repudiandae fugiat illo cupiditate excepturi esse officiis consectetur, laudantium qui voluptatem. Ad necessitatibus velit, accusantium expedita debitis impedit rerum totam id. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Natus quibusdam recusandae illum, nesciunt, architecto, saepe facere, voluptas eum incidunt dolores magni itaque autem neque velit in. At quia quaerat asperiores.</p>
                <!-- Service List -->
                <!-- The circle icons use Font Awesome's stacked icon classes. For more information, visit http://fontawesome.io/examples/ -->
                <div class="row">
                  <div class="col-lg-12">
                    <h2 class="page-header no-anchor">Categories</h2>
                  </div>
                  <div class="col-md-4">
                    <div class="panel panel-default text-center">
                        <div class="panel-heading">
                            <span class="fa-stack fa-5x">
                                  <i class="fa fa-circle fa-stack-2x text-primary"></i>
                                  <i class="fa fa-code fa-stack-1x fa-inverse"></i>
                            </span>
                        </div>
                        <div class="panel-body">
                          <h4 class="media-heading no-anchor">Personal Projects</h4>
                          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Illo itaque ipsum sit harum.</p>
                          <a href="projects.html" class="btn btn-primary">View Projects</a>
                        </div>
                    </div>
                  </div>
                  <div class="col-md-4">
                    <div class="panel panel-default text-center">
                        <div class="panel-heading">
                          <img class="card-img-top img-circle" src="img/projects/asrob.jpg" alt="ASROB featured image">
                        </div>
                        <div class="panel-body">
                          <h4 class="media-heading no-anchor">Projects at ASROB</h4>
                          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Illo itaque ipsum sit harum.</p>
                          <a href="projects.html" class="btn btn-primary">View Projects</a>
                        </div>
                    </div>
                  </div>
                  <div class="col-md-4">
                    <div class="panel panel-default text-center">
                        <div class="panel-heading">
                          <img class="card-img-top img-circle" src="img/projects/uc3music.png" alt="UC3Music featured image">
                        </div>
                        <div class="panel-body">
                          <h4 class="media-heading no-anchor">Projects at UC3Music</h4>
                          <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Illo itaque ipsum sit harum.</p>
                          <a href="projects.html" class="btn btn-primary">View Projects</a>
                        </div>
                    </div>
                  </div>
                </div>
            </div>
            <div class="tab-pane fade" id="service-tutorials">
              <h4 class="no-anchor">Tutorials</h4>
              <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quae repudiandae fugiat illo cupiditate excepturi esse officiis consectetur, laudantium qui voluptatem. Ad necessitatibus velit, accusantium expedita debitis impedit rerum totam id. Lorem ipsum dolor sit amet, consectetur adipisicing elit. Natus quibusdam recusandae illum, nesciunt, architecto, saepe facere, voluptas eum incidunt dolores magni itaque autem neque velit in. At quia quaerat asperiores.</p>
              <!-- Service List -->
              <!-- The circle icons use Font Awesome's stacked icon classes. For more information, visit http://fontawesome.io/examples/ -->
              <div class="row">
                <div class="col-lg-12">
                    <h2 class="page-header no-anchor">Featured Tutorials</h2>
                </div>
                <div class="col-md-4">
                  <div class="panel panel-default text-center">
                      <div class="panel-heading">
                        <img class="card-img-top" src="img/tutorials/pysidelogo-thumbnail.png" alt="PySide tutorial featured image">
                      </div>
                      <div class="panel-body">
                        <h4 class="media-heading no-anchor">PyQt/PySide</h4>
                        <p>Creating a PySide GUI application.</p>
                        <a href="https://david-estevez.gitbooks.io/tutorial-pyside-pyqt4/content/" class="btn btn-primary no_icon">View Tutorial</a>
                      </div>
                  </div>
                </div>
                <div class="col-md-4">
                  <div class="panel panel-default text-center">
                      <div class="panel-heading">
                        <img class="card-img-top" src="img/tutorials/gitlogo-thumbnail.png" alt="Git tutorial featured image">
                      </div>
                      <div class="panel-body">
                        <h4 class="media-heading no-anchor">The Git, the Bad and the Ugly</h4>
                        <p>Git for beginners (Spanish only).</p>
                        <a href="https://david-estevez.gitbooks.io/the-git-the-bad-and-the-ugly/content/es/" class="btn btn-primary no_icon">View Tutorial</a>
                      </div>
                  </div>
                </div>
                {% comment %} (To be enabled in the future)
                <div class="col-md-4">
                  <div class="panel panel-default text-center">
                      <div class="panel-heading">
                          <span class="fa-stack fa-5x">
                                <i class="fa fa-circle fa-stack-2x text-primary"></i>
                                <i class="fa fa-map-signs fa-stack-1x fa-inverse"></i>
                          </span>
                      </div>
                      <div class="panel-body">
                          <h4 class="no-anchor">All Tutorials</h4>
                          <p>List of all my tutorials.</p>
                          <a href="404.html" class="btn btn-primary">View Tutorials</a>
                      </div>
                  </div>
                </div>
                {% endcomment %}
              </div>
            </div>
        </div>
    </div>
</div>

{% include links.html %}
