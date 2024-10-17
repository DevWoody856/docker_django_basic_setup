# Basic Setup for Running Django with Docker

This is the repository for the blog post "<a href="https://rx-36.life/basic-setup-for-running-django-with-docker/" target="_blank">Basic setup for running Django with Docker.</a>"

## How to Download This Repo Locally and Run the Application

This description assumes the use of Docker and Windows 11.  
I use PyCharm as my IDE.


1. Enter following command from the command line.
```
git clone https://github.com/DevWoody856/docker_django_basic_setup.git
```

2. Navigate to the project root:

```bash
cd docker_django_basic_setup/
```

3. Create an `.env` file in the root of the project.

4. In the .env file you created, write the following.

```bash
DEBUG_VALUE=TRUE
SECRET_KEY=your_secret_key_here

DB_NAME=postgres
DB_USER=postgres
DB_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```

Note: DB_HOST is the service name of the database in docker-compose.yaml. In this Docker configuration, it is db. Also, ensure that the SECRET_KEY in settings.py is set to read from the .env file.

5. From the project root, enter the following command to build and start the Docker containers:

```bash
docker-compose up --build
```

6. If you successfully run `docker-compose up --build`, you should see the message:

```bash
Starting development server at http://0.0.0.0:8002/
```

7. Once it is up and running, please open another terminal while Docker is running, and enter the following command. This command enters the Docker container and launches the command line interface:

```bash
docker-compose exec backend bash
```
8. Inside the container, run the following command. While this blog post doesn't use any models, if you're building upon this example, you'll likely need them eventually. So, it's recommended to run migrations at this point:

```bash
python manage.py makemigrations
```

9. After that, run the migrate command.
```bash
python manage.py migrate
```

10. Let's also create a superuser:
```bash
python manage.py createsuperuser
```

11.The database setup is finished.

12. The application should already be running from step 5. You can access it at http://127.0.0.1:8002/ in your web browser. If it is not running, you can start the application inside the container with:
```bash
python manage.py runserver 0.0.0.0:8002
```

13. If  you get the following message, it is working.
```bash
Starting development server at http://127.0.0.1:8002/
```