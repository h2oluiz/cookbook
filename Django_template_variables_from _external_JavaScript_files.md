http://www.filipyoo.com/accessing-django-template-variables-from-external-javascript-files/

After having trouble with accessing Django variables for my blog posts, I managed after a lot a search and tests, a simple way to get it done. There's no mention about this on the Django official documentation, and I didn't find any helpful answer through StackOverflow.

So, for my blog, I have my view.py file which contains several classe-based views, and one of them is the view for the first page of the blog. This view returns a Django object of Post. Something like this :

class IndexView(generic.ListView):
	template_name = 'blog/index.html'
	context_object_name = 'all_posts_by_date'

	def get_queryset(self):
	    """Return all posts by posted dates."""
	    return list(Post.objects.order_by('-post_date'))
 

Then, in the Template index.html file, you have to declare a global variable to "store" the context_object_name returned by the view. For example :

> <script>
>     var posts_count = "{{ all_posts_by_date|length }}";
> </script>

> <script src="{% static 'blog/assets/js/createPageButton.js' %}"></script>
 

Your have to specify the external JavaScript file after the global variable assignment. So, all the external JavaScript files refered after the variable assignment, can use this variable without having to declare it again.

One thing to be careful, is that you can only use Django filter (e.g. |length) inside the Template html file and not in the external JavaScript file. If you want to use filters, use them inside the html template file before assigning variables. So now, you can access to your Django object variables, like this in for instance, the createPageButton.js :

> alert(posts_count);

So, I was able to keep the codes clean and modular, without writing the JavaScript functions inside the html file within a <script> tag !
