# Postgresql

## Docker Container

```cmd
docker run -d \
	--name datacourse \
	-e POSTGRES_PASSWORD=mysecretpassword \
	-e POSTGRES_USER=myusername \
	-e PGDATA=/var/lib/postgresql/data/pgdata \
	-p 5432:5432 \
	-v C:\\Users\\super\\Documents\\databases\\course:/var/lib/postgresql/data \
	-d postgres
```

```cmd
docker run -d --name postgrescourse -e POSTGRES_PASSWORD=mysecretpassword -e POSTGRES_USER=myusername -e PGDATA=/var/lib/postgresql/data/pgdata -p 5432:5432 -v C:\\Users\\super\\Documents\\databases\\postgrescourse:/var/lib/postgresql/data -d postgres
```

```cmd
docker run -d --name postgrescourse -e POSTGRES_PASSWORD=postgres -e POSTGRES_USER=postgres -e PGDATA=/var/lib/postgresql/data/pgdata -p 5432:5432 -v C:\\Users\\super\\Documents\\databases\\postgrescourse:/var/lib/postgresql/data -d postgres
```

To connect from the terminal:

```cmd
docker exec -it 22f42cd19ca9 psql -U myusername
```