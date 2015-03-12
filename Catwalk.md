# Catwalk #

## Installation ##

Install catwalk
```
easy_install catwalk
```

Then, in your controller, import catwalk

```
from catwalk.tg2 import Catwalk

from mypackage.model import DBSession, metadata
```

In your controller method, instantiate catwalk.
```
catwalk = Catwalk(DBSession, metadata)
```

You should then see a screen like this:

![http://tgtools.googlecode.com/svn/projects/catwalk/trunk/docs/images/catwalk_home.png](http://tgtools.googlecode.com/svn/projects/catwalk/trunk/docs/images/catwalk_home.png)


And if you click around, you can find forms like this:

![http://tgtools.googlecode.com/svn/projects/catwalk/trunk/docs/images/catwalk_form.png](http://tgtools.googlecode.com/svn/projects/catwalk/trunk/docs/images/catwalk_form.png)

## Securing Catwalk ##

By default, Catwalk is not secured. This is because it is up to the developer to provide the method for security, but it can easily be secured by extending the Catwalk controller object and using the secure controller methods provided by Turbogears. Here is an example code snippet to showing how you could secure your catwalk so that only admins can view it:

### Subclass Catwalk ###

```
from catwalk.tg2 import Catwalk
from repoze.what.predicates import in_group

class SecuredCatwalk(Catwalk):
    allow_only = in_group('manager')
```
### Instantiate Catwalk ###
```
catwalk = SecuredCatwalk(DBSession, metadata)
```