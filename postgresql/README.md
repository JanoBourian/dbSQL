# Postgresql

## Docker Container

```cmd
docker run -d \
	--name datacourse \
	-e POSTGRES_PASSWORD=mysecretpassword \
	-e POSTGRES_USER=myusername \
	-e PGDATA=/var/lib/postgresql/data/pgdata \
	-p 5432:5432 \
	-v C:\\Users\\super\\Documents\\databases\\FastAPI:/var/lib/postgresql/data \
	-d postgres
```

```cmd
docker run -d --name datacourse -e POSTGRES_PASSWORD=mysecretpassword -e POSTGRES_USER=myusername -e PGDATA=/var/lib/postgresql/data/pgdata -p 5432:5432 -v C:\\Users\\super\\Documents\\databases\\FastAPI:/var/lib/postgresql/data -d postgres
```
