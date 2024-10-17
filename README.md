# Basic setup for running Django with Docker

This is the repository for the blog post "<a href="https://rx-36.life/basic-setup-for-running-django-with-docker/" target="_blank">Basic setup for running Django with Docker.</a>"


## How to download this repo locally and running the application.  

This description assumes the use of docker and windows11.  
And I use pycharm for my IDE.


1. Enter following command from the command line.
```
git clone https://github.com/DevWoody856/docker_django_basic_setup.git
```

2. Enter following command in command line.
   (Go to projecto root)

```python
cd docker_django_basic/
```

3. Create an `.env` file in the root of the project.

4. In the .env file you created, write the following.

```python
DEBUG_VALUE=TRUE
SECRET_KEY=**************************************

DB_NAME=postgres
DB_USER=postgres
DB_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432

POSTGRES_DB=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
```

As a reminder, DB_HOST is the service name of the database in docker-compose.yaml.  
In this docker configuration, it is `db`.  
Also, this time the secret key is written directly in `settings.py`.

6. From the project root, enter the following command.

```bash
docker-compose up --build
```

7. If you success `docker-compose up -build`, you can see the message  
"starting development server at http://0.0.0.0:8002/".   
Once it is up and running, please **open another terminal** while docker running, enter the following command.
This is the command that enters the dokcer side and launches the command line.

```bash
docker-compose exec backend bash
```

8. When you are ready to enter a command, type the following command. While this blg post doesn't use any models, if you're building upon this example, you'll likely need them eventually. So, I recommend running migrations at this point.


```bash
python manage.py makemigrations
```

9. After that, run the migrate command.
```bash
python manage.py migrate
```

10. Let's also create a superuser.
```bash
python manage.py createsuperuser
```

11. Database set is finished.
Enter the following command and the application should start.
```bash
python manage.py runserver
```

12. If  you get the following message, it is working.
```bash
Starting development server at http://127.0.0.1:8002/
```