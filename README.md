# Fastapi Skeleton

A secure python fastapi development setup.

## Quick start

1. Clone the repo (if not done yet) and go inside the folder

2. Start the container (change the container name or other details if needed)

```bash
docker compose up -d; docker compose logs -f;
```

3. Visit the following urls to verify the working

```bash
http://127.0.0.1:8000/
http://127.0.0.1:8000/docs/
```

### if this is your first time to start the container than execute below steps as well.

4. Attach to the container (add the correct container name)

```bash
docker exec -it fastapi-dev /bin/bash
```

5. Correct the `venv` folder permission by executing the follow commands.

```bash
chown -R 1000:1000 ~/.cache/pip
chown -R 1000:1000 /opt/venv/
```

6. Exit from the attached container

7. Stop the container

```bash
docker compose down
```

8. Edit the `docker-compose.yaml` file. Find the line `#user: "${UID}:${GID}"` and remove the `#` from the begining. Save the file.

9. Start the container. Rhis is your secure container for python based fastapi development.

```bash
docker compose up -d; docker compose logs -f;
```

10. To install any additional pip packages than execute the `pip install` command as usual. Example

```bash
docker exec -it fastapi-dev pip install typer
```

## To delete the venv and reinstall everything

1. Start the container (if not running)

```bash
docker compose up -d;
```

2. Freez the requirment file

```bash
docker exec -it fastapi-dev pip freeze > /app/requirements.txt
```

3. Stop the container with delete volume flag
```bash
docker compose down -v
```

4. Start the container again. This will reinstall all the pip packages listed inside the `requirements.txt` file

```bash
docker compose up -d; docker compose logs -f;
```

5. Follow all the steps again from `step no 4` from `Quick Start` section.
