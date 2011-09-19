---
date: 2009-01-08 16:26:23
title: Keep your Django Applications in a Subfolder
layout: post
wordpress_url: http://solutions.treypiepmeier.com/2009/01/keep-your-django-applications-in-a-subfolder/
---
To keep your Django applications neatly filed into a subfolder (such as `apps/`), first add the following to your `settings.py`:

    import os
    PROJECT_ROOT = os.path.dirname(__file__)

Then in `manage.py`:

Right under ` #!/usr/bin/env python` add:

    import sys
    from os.path import abspath, dirname, join
    from site import addsitedir

Right before ` if __name__ == "__main__":` add:

    sys.path.insert(0, join(settings.PROJECT_ROOT, "apps"))

Now to figure out what to do in production...

### Source

- [Oebfare source code](http://github.com/brosner/oebfare/)