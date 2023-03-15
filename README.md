# Ecommerce_auction
Design an eBay-like e-commerce auction site  using the Django web framework, The tool and techniques which were used during the implementation of this project was: Django, python, javascript, HTML and CSS, SQL

How to work with query parameter in Django

In this case, I used a query parameter as an optional informational (show active listings, but from a specific category). So instead of building a new view and a new url path, I've used query parameter.

If you want to use query parameter, your hrefs must be like this:

"{% url 'activeListings'%}?category={{category.id}}"

where ?category={{category.id}} adds the optional category that will filter the listings.

In views.py, just do request.GET.get("category", None). This method gives you the value of the parameter called "category". If there's no value (no query parameter) found, it will give None as the default value
Troubleshoots
The view didn't return an HttpResponse object. It returned None instead

If you get "The view **** didn't return an HttpResponse object. It returned None instead", it's probably because your view method doesn't have a "return render" command. Check here the discussion
jango.db.utils.IntegrityError: NOT NULL constraint failed:

Instead of saving the form directly ...

form.save()

...try to do the following:

        newItem = form.save(commit=False)
        newItem.user = request.user <--- here you put all foreign key fields
        newItem.save()

TemplateSyntaxError at /auction/active default requires 2 arguments, 1 provided

Probably you are using the django template engine and you've put a whitespacce between arguments. For example, when there is no image to be shown, django will show a generic image:

This ir correct:

{{ image_path|default:"https://www.inbounder.com.br/wp-content/themes/inbounder/images/no-image/No-Image-Found-400x264.png"}}

But if I put a whitespace between the variable and the default, it won't work:

{{ image_path | default:"https://www.inbounder.com.br/wp-content/themes/inbounder/images/no-image/No-Image-Found-400x264.png"}}

HTML not loading local CSS file

I was working in my local CSS file, but nothing was changing on my website. The solution was to add "/" in the end of the "link" tag that makes reference to my css file

Before: <link rel="stylesheet" href="{% static 'auctions/styles.css' %}">

After : <link rel="stylesheet" href="{% static 'auctions/styles.css' %}/">
Page not found, but path is correctly set on urls.py

Solution: Open it using an incognito windows of your browser!
