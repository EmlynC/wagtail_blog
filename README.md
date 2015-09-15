# wagtail_blog
A WordPress-like blog app implemented in Wagtail.

# What is it

After reimplimenting WordPress-like blogs over and over again in Wagtail I decided to just make this. 
Feel free to use as is or copy it as a starting point. 
It's based on the Wagtail demo blog but is closer to a standard WordPress blog style. 

## Features

- Categories and tags with views
- RSS
- Basic starter templates with pagination
- Comments
- WordPress importer

Work in progress?

- Disqus comments

# Installation

1. `pip install wagtail-blog`
2. Add `blog` to INSTALLED_APPS
3. Add `url(r'^blog/', include('blog.urls', namespace="blog")),` to urls.py
4. `python manage.py migrate`
5. Override [templates](/blog/templates/blog/) as needed.

# Settings

`BLOG_PAGINATION_PER_PAGE` (Default 10) Set to change the number of blogs per page. Set to None to disable (useful if using your own pagination implementation).

# Import from WordPress

1. Enable WordPress JSON API
2. Create a Blog index page and note the title. Let's pretend my blog index page title is "blog"
3. Run `./manage.py wordpress_to_wagtail http://myblog.com blog username password` the username is your WordPress username with full access to the API. Without this you can't access all blog posts.

# Comments

django-comments-xtd comments work out of the box. Just install it as directed [here](http://django-comments-xtd.readthedocs.org/en/latest/). 
Customizing the xtd comment templates should be all you need - but feel free to review this app's templates which you may want to override.

Out of box Disqus coming someday - but it's pretty easy to add manually following the Disqus documentation and overriding templates.

Feel free to contribute other comment implimentations.

# Hacking

The included docker-compose file should make it easy to get up and running. 

1. Install docker and docker-compose
2. `docker-compose up`
3. `docker-compose run --rm web ./manage.py migrate`
4. `docker-compose run --rm web ./manage.py createsuperuser`
5. Log in and create a blog index page with blog pages to see a very basic implementation.
