# Django-rest-api

## Project setup:

1) Install Python 3.9 on your system.

2) Create a virtual environment for the project and activate it.

```
python3 -m venv env
source env/bin/activate
```

3) Create a new Django project and app:

```

django-admin startproject ProductApi
cd ProductApi
python manage.py startapp prodapp

```

4) Clone the repository and replace every file in your project except the settings.py file.

5) Install the required libraries using following command

```
pip install -r requirements.txt
```

6) Update the "settings.py" file from INSTALLED_APPS with following:

```
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'rest_framework',
    'corsheaders',
    'prodapp.apps.ProdappConfig',
    
]

CORS_ORIGIN_ALLOW_ALL = True

REST_FRAMEWORK = {
    'DEFAULT_RENDERER_CLASSES': [
        'rest_framework.renderers.JSONRenderer',
        'rest_framework.renderers.BrowsableAPIRenderer',
    ]
}

MIDDLEWARE = [
    'corsheaders.middleware.CorsMiddleware',
    'django.middleware.security.SecurityMiddleware',
    'django.contrib.sessions.middleware.SessionMiddleware',
    'django.middleware.common.CommonMiddleware',
    'django.middleware.csrf.CsrfViewMiddleware',
    'django.contrib.auth.middleware.AuthenticationMiddleware',
    'django.contrib.messages.middleware.MessageMiddleware',
    'django.middleware.clickjacking.XFrameOptionsMiddleware',
]

ROOT_URLCONF = 'productapi.urls'

TEMPLATES = [
    {
        'BACKEND': 'django.template.backends.django.DjangoTemplates',
        'DIRS': [],
        'APP_DIRS': True,
        'OPTIONS': {
            'context_processors': [
                'django.template.context_processors.debug',
                'django.template.context_processors.request',
                'django.contrib.auth.context_processors.auth',
                'django.contrib.messages.context_processors.messages',
            ],
        },
    },
]

WSGI_APPLICATION = 'productapi.wsgi.application'


# Database
# https://docs.djangoproject.com/en/4.0/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': BASE_DIR / 'db.sqlite3',
    }
}

APPEND_SLASH = False

# Password validation
# https://docs.djangoproject.com/en/4.0/ref/settings/#auth-password-validators

AUTH_PASSWORD_VALIDATORS = [
    {
        'NAME': 'django.contrib.auth.password_validation.UserAttributeSimilarityValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.MinimumLengthValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.CommonPasswordValidator',
    },
    {
        'NAME': 'django.contrib.auth.password_validation.NumericPasswordValidator',
    },
]


# Internationalization
# https://docs.djangoproject.com/en/4.0/topics/i18n/

LANGUAGE_CODE = 'en-us'

TIME_ZONE = 'UTC'

USE_I18N = True

USE_TZ = True


# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/4.0/howto/static-files/

STATIC_URL = 'static/'

# Default primary key field type
# https://docs.djangoproject.com/en/4.0/ref/settings/#default-auto-field

DEFAULT_AUTO_FIELD = 'django.db.models.BigAutoField'

```

7) Run app locally using:

```
python manage.py runserver
```

8) Create Superuser in database

```
python manage.py createsuperuser
```

9) In the browser access the api at

```
http://localhost:8000/api/products/
```


## Calling the API

Here are some curl requests to test the API:

1) Get all products:
```
curl http://localhost:8000/api/products/
```

2) Get a specific product by product_name:

```
curl http://127.0.0.1:8000/api/products/?search=<product_name>
```

3) Create a new product:

```
curl -X POST -H "Content-Type: application/json" -d '{"product_name":"New Product", "product_Category":"Category", "product_brand_name":"Brand", "product_img":""}' http://localhost:8000/api/products/
```

4) Update an existing product:

```
curl -X PUT -H "Content-Type: application/json" -d '{"product_name":"Updated Product", "product_Category":"Category", "product_brand_name":"Brand", "product_img":""}' http://localhost:8000/api/products/<product_id>/
```

5) To call the hosted API replace the "http://127.0.0.1:8000/" with "https://product-y6j6.onrender.com"
