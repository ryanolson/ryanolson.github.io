---
layout: post
title: Developing a Pragmatic RESTful API using Flask
---

## Why REST?

That question has been answered over and over again. Here are a couple good reviews:

- [Designing a RESTful API with Python and Flask](http://blog.miguelgrinberg.com/post/designing-a-restful-api-with-python-and-flask) by Miguel Grinberg
- [Best Practices for Designing a Pragmatic RESTful API](http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api) by Vinay Sahni

The [first article](http://blog.miguelgrinberg.com/post/designing-a-restful-api-with-python-and-flask)
does a great job of covering the basics of a RESTful interface, while the
[second article](http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api)
outlines the goals for our API.

The goal here is not to define a strict RESTful interface, but rather a pragmatic one.


## Flask Extensions (Classy +  RESTful + Restless)

[Flask](http://flask.pocoo.org/) is a superb microframe work.  This article will look at three
extensions to the Flask microframework that help simplify the creation of a RESTful API:

- [Flask-RESTful](https://github.com/twilio/flask-restful)
- [Flask-Classy](https://github.com/apiguy/flask-classy)
- [Flask-Restless](https://github.com/jfinkels/flask-restless)

Standalone, each of these extensions are first-class.

[Flask-RESTful](https://github.com/twilio/flask-restful) is almost perfect.

Pros:

Cons:
- `flask.ext.restful.Resource` based on `flask.views.MethodView`. 
    * this makes non-standard routes for aliasing common queries difficult,
    .e.g. `GET /tickets/recently_closed`
- Two `flask.ext.restful.Resource` objects are required for a typical resource
    * `GET /tickets` and `POST /tickets`
    * Full CRUD for `/tickets/<ticket_id>`

