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

```
COUNT(IF(Chat & inv check!="Correct" and Entry Date=TODAY(),1,0))+
COUNT(IF(Booking intimaion="FALSE" and Entry Date=TODAY(),1,0))+
COUNT(IF(Hotel confirmation message to customer="FALSE" and Entry Date=TODAY(),1,0))+
COUNT(IF(Rev ed start="FALSE" and Entry Date=TODAY(),1,0))+
COUNT(IF(Rev ed end="FALSE" and Return date=DATE(YEAR(TODAY()), MONTH(TODAY()), DAY(TODAY()) - 1),1,0))+
COUNT(IF(Vehicle status!="Assigned" and Journey date = DATE(YEAR(TODAY()), MONTH(TODAY()), DAY(TODAY()) + 1),1,0))+
COUNT(IF(Hotel status!="Booked-ack" and Entry Date=TODAY(),1,0))+
COUNT(IF(hp!="Paid" and Journey date=TODAY(),1,0))+
COUNT(IF(Bus/train/flight = 'Yes' and Entry Date=TODAY(),1,0))+
COUNT(IF(CV1 is null and D 1=TODAY(),1,0))+
COUNT(IF(CV2 is null and D 2=TODAY(),1,0))+
COUNT(IF(CV3 is null and D 3=TODAY(),1,0))+
COUNT(IF(tp!="Paid" and Return date=TODAY(),1,0))+
COUNT(IF(cp!="Paid" and Journey date=TODAY(),1,0))
```

```
COUNT(IF(Chat & inv check!="Correct" and Entry Date<TODAY(),1,0))+
COUNT(IF(Booking intimaion="FALSE" and Entry Date<TODAY(),1,0))+
COUNT(IF(Hotel confirmation message to customer="FALSE" and Entry Date<TODAY(),1,0))+
COUNT(IF(Rev ed start="FALSE" and Entry Date<TODAY(),1,0))+
COUNT(IF(Rev ed end="FALSE" and Return date<DATE(YEAR(TODAY()), MONTH(TODAY()), DAY(TODAY()) - 1),1,0))+
COUNT(IF(Vehicle status!="Assigned" and Journey date < DATE(YEAR(TODAY()), MONTH(TODAY()), DAY(TODAY()) + 1),1,0))+
COUNT(IF(Hotel status!="Booked-ack" and Entry Date<TODAY(),1,0))+
COUNT(IF(hp!="Paid" and Journey date<TODAY(),1,0))+
COUNT(IF(Bus/train/flight = 'Yes' and Entry Date<TODAY(),1,0))+
COUNT(IF(CV1 is null and D 1<TODAY(),1,0))+
COUNT(IF(CV2 is null and D 2<TODAY(),1,0))+
COUNT(IF(CV3 is null and D 3<TODAY(),1,0))+
COUNT(IF(tp!="Paid" and Return date<TODAY(),1,0))+
COUNT(IF(cp!="Paid" and Journey date<TODAY(),1,0))
```
