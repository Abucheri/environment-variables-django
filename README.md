# A simple example on how to configure enviroment variables in django

1. Create a django project of your own choice.
2. Create a .env file in the same directory where settings.py resides.
3. Put the contents that you want to be sucure into the .env file i.e

    SECRET_KEY=your_secret_key

    DATABASE_NAME=db_name
    DATABASE_USER=db_user
    DATABASE_PASSWORD=db_password
    DATABASE_HOST=db_host
    DATABASE_PORT=db_port

4. Install a package called django-environ for managing environment variables inside the project `pip Install django-environ`.
5. Inside settings, `import environ` from django environ and enable it to read the >.env file
## it can be done as shown below:
    import environ

    env = environ.Env()
    # reading .env file
    environ.Env.read_env()

    # Raises django's ImproperlyConfigured exception if SECRET_KEY not in os.environ
    SECRET_KEY = env("SECRET_KEY")

    DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': env("DATABASE_NAME"),
        'USER': env("DATABASE_USER"),
        'PASSWORD': env("DATABASE_PASSWORD"),
        'HOST': env("DATABASE_HOST"),
        'PORT': env("DATABASE_PORT"),
      }
    }

That's it, now you can Save the file and run the server everything should be working smoothly.  
You can also provide default values as shown below:

    SECRET_KEY = env("SECRET_KEY", default="unsafe-secret-key")

__Don't forget to add the .env file to ypur .gitignore before pushing your project to your repository. This is for security purposes__
