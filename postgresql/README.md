# Postgresql

## Docker Container

```bash
docker run -d \
	--name datacourse \
	-e POSTGRES_PASSWORD=mysecretpassword \
	-e POSTGRES_USER=myusername \
	-e PGDATA=/var/lib/postgresql/data/pgdata \
	-p 5432:5432 \
	-v C:\\Users\\super\\Documents\\databases\\course:/var/lib/postgresql/data \
	-d postgres
```

```bash
docker run -d --name postgrescourse -e POSTGRES_PASSWORD=mysecretpassword -e POSTGRES_USER=myusername -e PGDATA=/var/lib/postgresql/data/pgdata -p 5432:5432 -v C:\\Users\\super\\Documents\\databases\\postgrescourse:/var/lib/postgresql/data -d postgres
```

```bash
docker run -d --name postgrescourse -e POSTGRES_PASSWORD=postgres -e POSTGRES_USER=postgres -e PGDATA=/var/lib/postgresql/data/pgdata -p 5432:5432 -v C:\\Users\\super\\Documents\\databases\\postgrescourse:/var/lib/postgresql/data -d postgres
```

```bash
docker run -d --name postgresqlcourse -e POSTGRES_PASSWORD=password -e POSTGRES_USER=username -e PGDATA=/var/lib/postgresql/data/pgdata -p 5434:5432 -v C:\\Users\\super\\Documents\\databases\\postgresqlcourse:/var/lib/postgresql/data -d postgres
```

To connect from the terminal:

```bash
docker exec -it 22f42cd19ca9 psql -U myusername
```