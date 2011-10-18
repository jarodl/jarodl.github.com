---

title: Using the Disqus API from Python
layout: default

---

    # Init with your API key. To find out your key visit
    # http://disqus.com/api/get_my_key while logged in to disqus.com.
    disqus = Disqus(secret_key)

    # Get a list of forums that user owns
    disqus.forum_list()

    # Get a list of posts on a forum
    disqus.forum_posts(forum_id=1)

    # Get a list of categories on a forum
    disqus.categories_list(forum_id=2)

    # Get a list of threads on a forum
    disqus.thread_list(forum_id=2)

    # Get a list of updated threads on a forum
    disqus.updated_threads(forum_id=1)

    # Get a list of posts on a thread
    disqus.thread_posts(thread_id=1)

    # Get a particular thread or create it if it doesn't exist
    disqus.thread_by_identifier(forum_id=1, identifier='my_thread',
                            title='My Killer Thread')
    # or
    disqus.thread_by_url(url='http://my.awesome/thread')

    # Update a thread
    disqus.update_thread(forum_id=1, thread_id=4)

    # Create a new post
    disqus.create_post(site_id=1, thread_id=4,
                      message='Dope API, yo!')

The code is on [Github](https://github.com/jarodl/disqus.py).
