## Flask microblog

Just an implementation of [Miguel Grinberg's Flask based microblog](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world).
It's probably useful to link out to the [Flask](https://flask.palletsprojects.com/en/1.1.x/), [Jinja2](https://jinja.palletsprojects.com/en/2.11.x/) and [SQLAlchemy ORM](https://docs.sqlalchemy.org/en/13/) docs here though the concepts covered in the tutorial are pretty self-contained.

You can use this code but you're better off just going through the exercises yourself. 

I may have made changes, use at your own risk.

This is probably out of date and there might be better ways to learn Flask, but
this exercise has been pretty solid and no overt errors in the code so far. I
do sometimes have issues understanding where new code should be placed and I
find it useful to go check out the [example repo on GitHub](https://github.com/miguelgrinberg/microblog).
All chapters are tagged on the example repo for easy reference.

I've made some changes to formatting and have converted to use f-strings where
it makes code more readable.

#### Project layout
|Directory path    |Description|Contents |
|:-----------------|:----------|:-------------|
|`.`               | parent    | Contains config and entry files |
|`./app`           | app dir   | The HTTP routes and data models |
|`./app/templates` | templates | Jinja2 templates |
|`./migration`     | Alembic   | Migration repository |
|`/logs`           | logfiles  | app logs are here |

#### License
I have made this code MIT same as Grinberg's original 


### Random useful things documented here

All of this stuff is well documented already in the [Flask based microblog series](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world)
however I'm putting possibly useful information here so I don't have to
dig through docs to look this up later if I need it.


#### Schema changes

In [Ch. 4](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-iv-database) there are important
steps documented that need to be taken when you make a change to the db schema.

The first one is `flask db migrate` which examines the db as described in the
`models.py` and autogenerates a script to migrate from the current schema to
the new schema.  

```bash
flask db migrate -m "short description of changes"
```

The second command is `flask db upgrade` which runs the migration.

Note: Remember to check in the migration script under the `./migration/`
directory.

#### Creating and attaching to a virtual environment
Putting this here because I forget a lot.
```bash
# In Python 3.4 or newer run:
python3 -m venv venv
# In older python install virtualenv and run
virtualenv venv
```
Entering the virtual environment:
```bash
source venv/bin/activate
```
Exit the virtual environment
```bash
deactivate
```

#### Flask shell
There's a built in python REPL that's accessible using the `flask shell`
command and loads the entire operating environment for testing purposes.
This gets set up in the `microblog.py` parent command using the `app.shell_context_processor`
decorator and controls db models loaded.  If you want to automatically load
more models you'll need to configure it.

```python
from app import app, db
from app.models import User, Post

@app.shell_context_processor
def make_shell_context():
    return {'db': db, 'User': User, 'Post': Post}
```

See end of [Ch. 4](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-iv-database)
for more useful info.

#### Setting up error mailing and testing

This is in [Ch. 7](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-vii-error-handling) along with error pages.

Use these environment variables to send errors through gmail:
```bash
export MAIL_SERVER=smtp.googlemail.com
export MAIL_PORT=587
export MAIL_USE_TLS=1
export MAIL_USERNAME=<your-gmail-username>
export MAIL_PASSWORD=<your-gmail-password>
```

To test email you can run a test mail server using python:

```bash
python -m smtpd -n -c DebuggingServer localhost:8025
```

You can then configure the webapp to use this server by setting the following
variables:
```bash
export MAIL_SERVER=localhost
export MAIL_PORT=8025
```

#### Unit tests
In [Ch. 8](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-viii-followers/page/0#comments)
there are some unit tests using the `unittest` framework and can be run with `python tests.py`

### Notes to myself

Currently on [Ch. 13](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-xiii-i18n-and-l10n)

#### Things to do before committing

1. Save the pip requirements `pip freeze > requirements.txt` if the requirements
   change
2. Update the current chapter in the readme
3. If a db migration has occurred, make sure to check in the migration script

