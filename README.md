# [Django Datatables Sample](https://django-datatables-sample.appseed.us/)

> Playground starter to manage a DataRable in Django - [LIVE Demo](https://django-datatables-sample.appseed.us/)

- ✅ Load sample data using admin section
- ✅ Inline rows edit activated at double click
- ✅ Pagination and Search  
- ✅ Deployment scripts: `Docker`
- ✅ Free [Support](https://appseed.us/support/) via `Email` and `Discord`

<br /> 

> 🚀 `PROMO`: **[Junior Developers Starter KIT](https://www.creative-tim.com/product/buy/bundle/junior-bundle?AFFILIATE=128200)** `85%OFF`

The package includes a `rock-solid collection of premium assets` (**Kits & Dashboards**) that can be used to build eye-catching portfolios and web apps in no time.

[![Junior Developers Starter KIT](https://user-images.githubusercontent.com/51854817/195055646-e55200cd-0ddd-4bdd-aded-0d4e4479789b.png)](https://www.creative-tim.com/product/buy/bundle/junior-bundle?AFFILIATE=128200)

<br /> 

## How to use it

```bash
$ # Get the code
$ git clone https://github.com/app-generator/django-datatables-sample.git
$ cd django-datatables-sample
$
$ # Virtualenv modules installation (Unix based systems)
$ virtualenv env
$ source env/bin/activate
$
$ # Virtualenv modules installation (Windows based systems)
$ # virtualenv env
$ # .\env\Scripts\activate
$
$ # Install modules - SQLite Storage
$ pip3 install -r requirements.txt
$
$ # Create tables
$ python manage.py makemigrations
$ python manage.py migrate
$
$ # Create app superuser
$ python manage.py createsuperuser
$
$ # Start the application (development mode)
$ python manage.py runserver # default port 8000
$
$ # Start the app - custom port
$ # python manage.py runserver 0.0.0.0:<your_port>
$
$ # Access the web app in browser: http://127.0.0.1:8000/
```

> Note: To use the app, please access the registration page and create a new user. After authentication, the app will unlock the private pages.

<br />

## Load Data For Datatable

In Django admin, you can import data for the **Transaction** section. 
To do this just click on ```IMPORT``` button then select your csv, xls or etc file and submit it.

![Import Data](https://raw.githubusercontent.com/app-generator/django-datatables-sample/master/media/transactions_screenshot_3.png)

> Sample **[Data](https://github.com/app-generator/django-datatables-sample/blob/master/sample_data/transactions_data.csv)**

### Datatable for transactions
* Imported information is displayed in the **Transactions** section. 

![Django Dashboard Volt - Template project provided by AppSeed.](https://raw.githubusercontent.com/app-generator/django-datatables-sample/master/media/transactions_screenshot_1.png)

* In this section, you can *search*, *edit*, and *delete* the transactions. The added features of this **datatable** are:
    - Paginated information (transaction page) with usable controls: PREV, 1,2,3., NEXT
    - Search box to filter
    - Delete row control
    - edit cel data on double click and ENTER on confirm.

![Django Dashboard Volt - Template project provided by AppSeed.](https://raw.githubusercontent.com/app-generator/django-datatables-sample/master/media/transactions_screenshot_2.png)
 
<br>

## Code-base structure

The project is coded using a simple and intuitive structure presented bellow:

```bash
< PROJECT ROOT >
   |
   |-- core/                               # Implements app logic and serve the static assets
   |    |-- settings.py                    # Django app bootstrapper
   |    |-- wsgi.py                        # Start the app in production
   |    |-- urls.py                        # Define URLs served by all apps/nodes
   |    |
   |    |-- static/
   |    |    |-- <css, JS, images>         # CSS files, Javascripts files
   |    |
   |    |-- templates/                     # Templates used to render pages
   |         |
   |         |-- includes/                 # HTML chunks and components
   |         |    |-- navigation.html      # Top menu component
   |         |    |-- sidebar.html         # Sidebar component
   |         |    |-- footer.html          # App Footer
   |         |    |-- scripts.html         # Scripts common to all pages
   |         |
   |         |-- layouts/                  # Master pages
   |         |    |-- base-fullscreen.html # Used by Authentication pages
   |         |    |-- base.html            # Used by common pages
   |         |
   |         |-- accounts/                 # Authentication pages
   |         |    |-- login.html           # Login page
   |         |    |-- register.html        # Register page
   |         |
   |      index.html                       # The default page
   |     page-404.html                     # Error 404 page
   |     page-500.html                     # Error 404 page
   |       *.html                          # All other HTML pages
   |
   |-- authentication/                     # Handles auth routes (login and register)
   |    |
   |    |-- urls.py                        # Define authentication routes  
   |    |-- views.py                       # Handles login and registration  
   |    |-- forms.py                       # Define auth forms  
   |
   |-- app/                                # A simple app that serve HTML files
   |    |
   |    |-- views.py                       # Serve HTML pages for authenticated users
   |    |-- urls.py                        # Define some super simple routes  
   |
   |-- requirements.txt                    # Development modules - SQLite storage
   |
   |-- .env                                # Inject Configuration via Environment
   |-- manage.py                           # Start the app - Django default start script
   |
   |-- ************************************************************************
```

<br />

> The bootstrap flow

- Django bootstrapper `manage.py` uses `core/settings.py` as the main configuration file
- `core/settings.py` loads the app magic from `.env` file
- Redirect the guest users to Login page
- Unlock the pages served by *app* node for authenticated users

<br />

## Deployment

The app is provided with a basic configuration to be executed in [Docker](https://www.docker.com/), [Gunicorn](https://gunicorn.org/), and [Waitress](https://docs.pylonsproject.org/projects/waitress/en/stable/).

### [Docker](https://www.docker.com/) execution
---

The application can be easily executed in a docker container. The steps:

> Get the code

```bash
$ git clone https://github.com/app-generator/django-datatables-sample.git
$ cd django-datatables-sample
```

> Start the app in Docker

```bash
$ sudo docker-compose pull && sudo docker-compose build && sudo docker-compose up -d
```

Visit `http://localhost:5005` in your browser. The app should be up & running.

<br />

### [Gunicorn](https://gunicorn.org/)
---

Gunicorn 'Green Unicorn' is a Python WSGI HTTP Server for UNIX.

> Install using pip

```bash
$ pip install gunicorn
```
> Start the app using gunicorn binary

```bash
$ gunicorn --bind=0.0.0.0:8001 core.wsgi:application
Serving on http://localhost:8001
```

Visit `http://localhost:8001` in your browser. The app should be up & running.


<br />

### [Waitress](https://docs.pylonsproject.org/projects/waitress/en/stable/)
---

Waitress (Gunicorn equivalent for Windows) is meant to be a production-quality pure-Python WSGI server with very acceptable performance. It has no dependencies except ones that live in the Python standard library.

> Install using pip

```bash
$ pip install waitress
```
> Start the app using [waitress-serve](https://docs.pylonsproject.org/projects/waitress/en/stable/runner.html)

```bash
$ waitress-serve --port=8001 core.wsgi:application
Serving on http://localhost:8001
```

Visit `http://localhost:8001` in your browser. The app should be up & running.

<br />

## Credits & Links

- [Django](https://www.djangoproject.com/) - The official website
- [Boilerplate Code](https://appseed.us/boilerplate-code) - Index provided by **AppSeed**
- [Boilerplate Code](https://github.com/app-generator/boilerplate-code) - Index published on Github

<br />

---
[Django Datatables Sample](https://django-datatables-sample.appseed.us/) - Provided by **AppSeed** [Web App Generator](https://appseed.us/app-generator).
