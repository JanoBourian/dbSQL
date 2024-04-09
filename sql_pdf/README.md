```bash
docker run -d --name sqlpdf -e POSTGRES_PASSWORD=mysecretpassword -e POSTGRES_USER=myusername -e PGDATA=/var/lib/postgresql/data/pgdata -p 5433:5432 -v C:\\Users\\super\\Documents\\databases\\sqlpdf:/var/lib/postgresql/data -d postgres
```