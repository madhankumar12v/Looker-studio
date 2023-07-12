### Backup formula

```
CASE
  WHEN Hotel confirmation message to customer="FALSE" and Entry Date=TODAY() THEN 'Today'
  WHEN Hotel confirmation message to customer="FALSE" and Entry Date<TODAY() THEN 'Overdue'
  ELSE NULL
END
```

```
CASE
  WHEN Rev ed start="FALSE" and Entry Date=TODAY() THEN 'Today'
  WHEN Rev ed start="FALSE" and Entry Date<TODAY() THEN 'Overdue'
  ELSE NULL
END
```

```
CASE
  WHEN Rev ed end="FALSE" and Entry Date=TODAY() THEN 'Today'
  WHEN Rev ed end="FALSE" and Entry Date<TODAY() THEN 'Overdue'
  ELSE NULL
END
```

```
CASE
  WHEN Chat & inv check!="Correct" and Entry Date=TODAY() THEN 'Today'
  WHEN Chat & inv check!="Correct" and Entry Date<TODAY() THEN 'Overdue'
  ELSE NULL
END
```

```
CASE
  WHEN Vehicle status!="Assigned" and Journey date = DATE(YEAR(TODAY()), MONTH(TODAY()), DAY(TODAY()) + 1) THEN 'Today'
  WHEN Vehicle status!="Assigned" and Journey date < DATE(YEAR(TODAY()), MONTH(TODAY()), DAY(TODAY()) + 1) THEN 'Overdue'
  ELSE NULL
END
```

```
CASE
  WHEN Hotel status!="Booked-ack" and Entry Date=TODAY() THEN 'Today'
  WHEN Hotel status!="Booked-ack" and Entry Date<TODAY() THEN 'Overdue'
  ELSE NULL
END
```
