---
layout: post
title: Developing a Pragmatic RESTful API using Flask
published: false
---

## Why REST?

That question has been answered over and over again. Here are a couple good reviews:

- [Designing a RESTful API with Python and Flask](http://blog.miguelgrinberg.com/post/designing-a-restful-api-with-python-and-flask) by Miguel Grinberg
- [Best Practices for Designing a Pragmatic RESTful API](http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api) by Vinay Sahni

The [first article](http://blog.miguelgrinberg.com/post/designing-a-restful-api-with-python-and-flask)
does a great job of covering the basics of a RESTful interface, while the
[second article](http://www.vinaysahni.com/best-practices-for-a-pragmatic-restful-api)
outlines the goals for our API.

The goal here is to define a pragmatic RESTful API, not necessarily a strict RESTful API.


## Flask Extensions (Classy +  RESTful + Restless)

[Flask](http://flask.pocoo.org/) is a superb microframework.  This article will look at three
extensions to the Flask microframework that help simplify the creation of a RESTful API:

- [Flask-RESTful](https://github.com/twilio/flask-restful)
- [Flask-Classy](https://github.com/apiguy/flask-classy)
- [Flask-Restless](https://github.com/jfinkels/flask-restless)

Standalone, each of these extensions are first-class.  However, each project has some limitations
which can be alievated by combining them.

### Flask-RESTful

#### Pros:
- Error handling
- [Request Parsing](http://flask-restful.readthedocs.org/en/latest/reqparse.html)
- Works with any data model

#### Cons:
- `flask.ext.restful.Resource` based on `flask.views.MethodView`. 
    * this makes non-standard routes for aliasing common queries difficult,
    .e.g. `GET /tickets/recently_closed`
- Two `flask.ext.restful.Resource` objects are required for a typical resource
    1. `GET /tickets` and `POST /tickets`
    2. Full CRUD for `/tickets/<ticket_id>`

### Flask-Classy

#### Pros:
- Extendable `FlaskView` allowing `INDEX`, `GET`, `POST`, `PUT`, `PATCH` and `DELETE`, plus
  [custom routes](https://pythonhosted.org/Flask-Classy/#using-custom-routes)

#### Cons:
- Two issues with pull requests that need to be merged: 
  [Issue #60](https://github.com/apiguy/flask-classy/pull/60) and
  [Issue #61](https://github.com/apiguy/flask-classy/pull/61)
    * availabe at [ryanolson/flask-classy](https://github.com/ryanolson/flask-classy)
    
### Flask-Restless

#### Pros:
- Great tools for working with SQLAlchemy models, namely `flask.ext.restless.helpers.to_dict`

#### Cons
- Restricted use with SQLAlchemy models



