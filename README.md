# productscout

This project is scaffolded by [Yeoman](http://yeoman.io). See [generator-vars-django](https://github.com/VARIANTE/generator-vars-django.git) for more details.

## Usage

Install node modules if they are not already installed:
```
$ npm install
```

Initialize ```virtualenv``` if needed:
```
$ virtualenv {path}
```

Add generated environment variables in ```./.secrets``` to ```{virtualenv_path}/bin/activate``` if needed.

(Re)activate ```virtualenv```:
```
$ source {virtualenv_path}/bin/activate
```

Install ```pip``` dependencies using ```./requirements.txt``` they are not already installed:
```
$ pip install -r requirements.txt
```

Verify ```pip``` dependencies installed correctly under ```virtualenv```:
```
$ which django-admin.py
```

Update environment variables in ```{virtualenv_path}/bin/activate``` with new database configs.

Apply initial migration:
```
$ npm run migrate
```

Test dev environment. You should see "Hello, World!":
```
$ npm run dev
```

Test prod environment. You should see "Hello, World!":
```
$ npm run prod
```

## Tasks

```$ npm run dev```: Compiles all source files, serves the site and watches for file changes. Best used during development.

```$ npm run prod```: Builds the entire project in production.

All tasks are broken into micro Gulp tasks, check out the ```tasks``` folder for more details. Also see ```tasks/.taskconfig``` for more custom flags such as ```--skip-js-min```, ```--skip-css-min```, etc.

## Common Issues

1. If Nginx cannot serve the project (getting a 500 Internal Error or something like that), check the error logs at ```/var/log/nginx/error.log```.

2. If you get an error about permission issues with writing to the UDP socket upon starting the uWSGI emperor, you might need to change the owner of the project directory to the Nginx owner/group, which is probably `www-data:www-data`

3. If you are getting a 400 error, you can debug this using your browser console to see what is wrong. If you get a GET request fail on the domain itself, chances are you forgot to add your domain to the ALLOWED_HOSTS of your Django project settings.

4. If you are getting a 500 error, enable DEBUG in project/settings/prod.py. It could be something trivial.

## License

This software is released under the [MIT License](http://opensource.org/licenses/MIT).
