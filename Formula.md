### Text to Date convert

```
PARSE_DATE("%Y-%m-%d", YourTextField)

```
### Count the Specific Text using Count+IF Function

```
COUNT(IF(status="confirmed",1,null))
```
### Sum the Specific text Respective cost using Sum+IF Function

```
SUM(if(status="quote sent",Our cost,null))
```

### Count the specific text and also Concat Both Column 

```
CONCAT(COUNT(Campaing name),"/",COUNT(status))
```

### Display the specific text when condition is true 

```
IF(Booking intimaion="FALSE","Pending","Completed")
```

### Display the Specific text and count also when apply multiple condition is true 

```
CASE
  WHEN Chat & inv check = 'Issue' THEN 'Pending'
  WHEN Chat & inv check = '.' THEN 'Pending'
  ELSE NULL
END
```

### Display the Specific text and count also when apply multiple condition is true 
```
CASE
  WHEN Hotel status = 'Yet' THEN 'Pending'
  WHEN Hotel status = 'Requested' THEN 'Pending'
    WHEN Hotel status = 'Booked' THEN 'Pending'
      WHEN Hotel status = 'NA' THEN 'Pending'
  ELSE NULL
END
```

### If want diplay today date tick checkbox other wise exclude today date
```
Entry Date<TODAY()
```

### Count the Specific Text using Count+IF Function
```
COUNT(IF(Booking intimaion="FALSE",1,Null))+COUNT(IF(Hotel confirmation message to customer="FALSE",1,Null))+COUNT(IF(Rev ed start="FALSE",1,Null))+COUNT(IF(Rev ed end="FALSE",1,Null))+COUNT(IF(Chat & inv check="Correct",Null,1))+COUNT(IF(Vehicle status="Assigned",Null,1))+COUNT(IF(Hotel status="Booked-ack",Null,1))
```

### Count the Specific Text using Count+IF Function (show today only) Include today only
```
COUNT(IF(advance reciept="FALSE" and Date=TODAY(),1,Null))+COUNT(IF(booking conf message="FALSE" and Date=TODAY(),1,Null))+COUNT(IF(Remainder message="FALSE" and Date=TODAY(),1,Null))+COUNT(IF(Driver<->customer swap="FALSE" and Date=TODAY(),1,Null))+COUNT(IF(survey s1="FALSE" and Date=TODAY(),1,Null))+COUNT(IF(Final invoice="FALSE" and Date=TODAY(),1,Null))+COUNT(IF(survey 2="FALSE" AND Date=TODAY(),1,NULL))
```
### Group by Week 
```
CASE
  WHEN DAY(Date) <= 7 THEN "Week 1 | 1-7"
  WHEN DAY(Date) <= 14 THEN "Week 2 | 8-14"
  WHEN DAY(Date) <= 21 THEN "Week 3 | 15-21"
  WHEN DAY(Date) <= 31 THEN "Week 4 | 22-31"
  ELSE "Invalid Date"
END
```

### Group by month
```
CASE
  WHEN REGEXP_MATCH(Journey date, r'\d{4}-\d{2}-\d{2}') THEN
    CASE
      WHEN REGEXP_MATCH(Journey date, r'(\d{4})-(\d{2})-(\d{2})') THEN
        CASE
          WHEN REGEXP_EXTRACT(Journey date, r'-(\d{2})-') = '01' THEN 'January'
          WHEN REGEXP_EXTRACT(Journey date, r'-(\d{2})-') = '02' THEN 'February'
          WHEN REGEXP_EXTRACT(Journey date, r'-(\d{2})-') = '03' THEN 'March'
          WHEN REGEXP_EXTRACT(Journey date, r'-(\d{2})-') = '04' THEN 'April'
          WHEN REGEXP_EXTRACT(Journey date, r'-(\d{2})-') = '05' THEN 'May'
          WHEN REGEXP_EXTRACT(Journey date, r'-(\d{2})-') = '06' THEN 'June'
          WHEN REGEXP_EXTRACT(Journey date, r'-(\d{2})-') = '07' THEN 'July'
          WHEN REGEXP_EXTRACT(Journey date, r'-(\d{2})-') = '08' THEN 'August'
          WHEN REGEXP_EXTRACT(Journey date, r'-(\d{2})-') = '09' THEN 'September'
          WHEN REGEXP_EXTRACT(Journey date, r'-(\d{2})-') = '10' THEN 'October'
          WHEN REGEXP_EXTRACT(Journey date, r'-(\d{2})-') = '11' THEN 'November'
          WHEN REGEXP_EXTRACT(Journey date, r'-(\d{2})-') = '12' THEN 'December'
        END
    ELSE NULL
    END
  ELSE NULL
END
```

### Group by Week 
```
CASE
  WHEN REGEXP_MATCH(Journey date, r'\d{4}-\d{2}-\d{2}') THEN
    CASE
      WHEN REGEXP_MATCH(Journey date, r'(\d{4})-(\d{2})-(\d{2})') THEN
        CASE
          WHEN EXTRACT(DAY FROM PARSE_DATE('%Y-%m-%d', Journey date)) <= 7 THEN 'Week 1 | 1-7'
          WHEN EXTRACT(DAY FROM PARSE_DATE('%Y-%m-%d', Journey date)) <= 14 THEN 'Week 2 | 8-14'
          WHEN EXTRACT(DAY FROM PARSE_DATE('%Y-%m-%d', Journey date)) <= 21 THEN 'Week 3 | 15-21'
          WHEN EXTRACT(DAY FROM PARSE_DATE('%Y-%m-%d', Journey date)) <= 31 THEN 'Week 4 | 22-31'
          ELSE 'Invalid date'
        END
      ELSE NULL
    END
  ELSE NULL
END
```

### Display the Specific text and count also when apply multiple condition is true 
```
CASE
  WHEN DateField IS NOT NULL THEN "Completed"
  ELSE "Not Completed"
END

