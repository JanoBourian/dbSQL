# Building up a Database

## Create statements

```sql
CREATE SCHEMA fake;
CREATE TABLE IF NOT EXISTS fake.fake_survey_information(
    id UUID,
    score SMALLINT,
    created_at TIMESTAMP
);

INSERT INTO fake.fake_survey_information(score_id, score, created_at)
VALUES (gen_random_uuid(), floor(random() * 5 + 1)::int, now());
```

```sql
```

```sql
```

```sql
```

```sql
```