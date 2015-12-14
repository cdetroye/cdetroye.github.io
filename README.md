# Researcher's blog

This is a minimal working example for a research blog. It is based on templates
I found online, extended with bits and pieces to make it easier to use.

## What it does

 - It uses `jekyll-scholar` to make it easy to cite papers in a blogpost and/or build bibliographies.
 - It has Google Analytics ready for use.
 - It is fairly straight forward to add Disqus comments to individual posts
 - It has mathjax enabled so you can type in some fancy greek.

## Initial setup

There is some setup involved to get this blog up and running for you
personally. We will go over each part.

### Comments

To enable comments you will need a Disqus account. Go over to
https://disqus.com/ and create an account. After you have set that up and have
verified your account you should be able to add Disqus to your website by going
to https://disqus.com/admin/create/. Follow the tutorial and then you should see
the code to add Disqus to a universal webpage. An example might look like the
one below. Once you have this code, replace the existing code in
`_includes/comments.html` with yours. Be sure to keep in the if-test!


```
<div id="disqus_thread"></div>
<script>
    /**
     *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
     *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables
     */
    /*
    var disqus_config = function () {
        this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
        this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
    */
    (function() {  // DON'T EDIT BELOW THIS LINE
        var d = document, s = d.createElement('script');
        
        s.src = '//christophedetroyer.disqus.com/embed.js';
        
        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>
```

### Google Analytics

To enable analytics you will have to create a free account on
http://www.google.com/analytics/. Again, you will get some simple
copy/paste-able code. Replace the code in `_include/google_analytics.html` with
your own code.

If you don't want fancy analytics you can simply turn them off by removing the
line `{% include google_analytics.html %}` from the `_layout/default.html` page.


### Citations

Citations are a bit of a trick to get working. You can either use them to list
your own publications, or to actually add resources to a webpost. For your own
publications, create a `.bib` file for each type of publication you want. E.g.,
`books.bib`, `journals.bib` etc.

For all the works you just cite in blogposts you can create a file `all.bib` and
just append all your citations from all your blogposts to that. Unless, of
course, you want to keep them seperate. But I will not go into that.

TODO Explain all the stuffs here.

### Mathjax

Mathjax is a very powerful Latex renderingtool in JavaScript. However, it is not
as simple as copy-pasting some code in between `$$`. I have provided a few
abstractions (mathpartir in particular) in a file `_includes/mathjax.html`. If
you want to write using these abstractions, make sure to include them in every
blog post you need them in by adding the `{% include mathjax.html %}` directive
to the top of your post.

Then it is somewhat easier to paste mathpartir code in there.
