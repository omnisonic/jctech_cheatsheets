### Official Jinja 2 Documentation

[https://jinja.palletsprojects.com/en/3.0.x/templates/](https://jinja.palletsprojects.com/en/3.0.x/templates/)


### Inherit from the base.html template 

```
{% extends "base.html" %}
```

### Placeholder in base or parent for the child to override

```
{% block your_block_name%} {% endblock%}
```

### Placeholder override in child

```
{% block your_block_name%} your_stuff {% endblock%}
```

### Get the content of parent block with {{super()}}

```
{% block your_bock_name %}
    your_child_stuff
    {{ super() }}
{% endblock %}
```

### Pelican - insert the sitename

```
{{ SITENAME }}
```

### Pelican - insert the summary of the article (eg in the index.html template)

```
{{ article.summary }}
```

### Pelican -  insert a link to an article url

```
<a href="{{ SITEURL }}/{ {article.url }}">article title</a>
```

### Pelican - for every article (eg in the index.html template)

```
{% for article in articles_page.object_list %}
<your html and more jijma templating goes here and is repeated for each article (.md file) that exists in your content folder. This is for building your summaries of your blog articles on the blog index page>
{% endfor %}
```
### If Else logic nested in for loop

```
{% for thing in things %}
    {% if some_condition %}
     Do something only for this condition
    {% else %}
        Do this instead
    {% endif %}
    {% endfor %}
       
```

### Basic usage

```
- variable x has content: {{ x }}
- expression: {{ x + 1 }}
- escaped for HTML: {{ x | e }}
```

### Control structures

```
{% for x in range(5) %}
    {% if x % 2 == 0 %}
        {{ x }} is even!
    {% else %}
        {{ x }} is odd!
    {% endif %}
{% endfor %}
```

### Whitespace trimming

```
these are
{{ "three" }}
lines.

this is conc
{{- "at" -}}
enated.
```

### Special blocks

```
{% filter e %}{% endraw %}
{ {%- if 0 -%}{%- endif -%} % raw %}
{%- raw -%}
    This is a raw block where {{nothing is evaluated}}
    {% not even this %}
    and <html is escaped> too with "e" filter
{% endraw %}
{ {%- if 0 -%}{%- endif -%} % endraw %}{% raw %}
{% endfilter %}

{% macro myfunc(x) %}
    this is a reusable macro, with arguments: {{x}}
{% endmacro %}

{{ myfunc(42) }}

{#
this is a comment
#}
```


### Inheritance

#### shared.html

```
<html>
  <head>
    <title>{%block title %}{% endblock %}</title>
  </head>
  <body>
    <header><h1>{% block title %}{% endblock %}</h1></header>
    <main>{% block content %}{% endblock %}</main>
  </body>
</html>
```

#### home.html

```
{% extends "shared.html" %}
{% block title %}Welcome to my site{% endblock %}
{% block content %}
This is the body
{% endblock %}
```

## Library

### Basic usage

```python
from jinja2 import Template
template = Template('Hello {{ name }}!')
template.render(name='John Doe') == u'Hello John Doe!'
```

{% endraw %}
