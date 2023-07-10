

#### Today_SalesTask
```
COUNT(IF(survey s1="FALSE" and Entry Date=TODAY(),1,0))+
COUNT(IF(survey 2="FALSE" and Journey date=TODAY(),1,0))+
COUNT(IF(advance reciept="FALSE" and Entry Date=TODAY(),1,0))+
COUNT(IF(booking conf message="FALSE" and Entry Date=TODAY(),1,null))+
COUNT(IF(Remainder message="FALSE" and Journey date = DATE(YEAR(TODAY()), MONTH(TODAY()), DAY(TODAY()) - 1),1, NULL))+
COUNT(IF(Driver<->customer swap="FALSE" and Journey date = DATE(YEAR(TODAY()), MONTH(TODAY()), DAY(TODAY()) - 1),1,null))+
COUNT(IF(Attemp Date=TODAY(),1,null))+
COUNT(IF(Followup date=TODAY(),1,null))+
COUNT(IF(Final invoice="FALSE" and Return date=TODAY(),1,null))
```
#### Overdue_salesTask

```
COUNT(IF(survey s1="FALSE" and Entry Date>TODAY(),1,null))+
COUNT(IF(survey 2="FALSE" and Journey date>TODAY(),1,null))+
COUNT(IF(advance reciept="FALSE" and Entry Date>TODAY(),1,null))+
COUNT(IF(booking conf message="FALSE" and Entry Date>TODAY(),1,null))+
COUNT(IF(Remainder message="FALSE" and Journey date > DATE(YEAR(TODAY()), MONTH(TODAY()), DAY(TODAY()) - 1), 1, NULL))+
COUNT(IF(Driver<->customer swap="FALSE" and Journey date > DATE(YEAR(TODAY()), MONTH(TODAY()), DAY(TODAY()) - 1),1,null))+
COUNT(IF(Attemp Date>TODAY(),1,null))+
COUNT(IF(Followup date>TODAY(),1,null))+
COUNT(IF(Final invoice="FALSE" and Return date>TODAY(),1,null))
```

#### 1.Survey s1_task

```
CASE
  WHEN survey s1="FALSE" and Entry Date=TODAY() THEN 'Today'
  WHEN survey s1="FALSE" and Entry Date>TODAY() THEN 'Overdue'
  ELSE NULL
END
```

#### 2.survey 2_task

```
CASE
  WHEN survey 2="FALSE" and Journey date=TODAY() THEN 'Today'
  WHEN survey 2="FALSE" and Journey date>TODAY() THEN 'Overdue'
  ELSE NULL
END
```

#### 3.advance reciept_task

```
CASE
  WHEN advance reciept="FALSE" and Entry Date=TODAY() THEN 'Today'
  WHEN advance reciept="FALSE" and Entry Date>TODAY() THEN 'Overdue'
  ELSE NULL
END
```

#### 4.booking conf message_task

```
CASE
  WHEN booking conf message="FALSE" and Entry Date=TODAY() THEN 'Today'
  WHEN booking conf message="FALSE" and Entry Date>TODAY() THEN 'Overdue'
  ELSE NULL
END
```

#### 5.Remainder message _task

```
CASE
  WHEN Remainder message="FALSE" and Journey date = DATE(YEAR(TODAY()), MONTH(TODAY()), DAY(TODAY()) - 1) THEN 'Today'
  WHEN Remainder message="FALSE" and Journey date > DATE(YEAR(TODAY()), MONTH(TODAY()), DAY(TODAY()) - 1) THEN 'Overdue'
  ELSE NULL
END
```

#### 6.Driver<->customer swap_task

```
CASE
  WHEN Driver<->customer swap="FALSE" and Journey date = DATE(YEAR(TODAY()), MONTH(TODAY()), DAY(TODAY()) - 1) THEN 'Today'
  WHEN Driver<->customer swap="FALSE" and Journey date > DATE(YEAR(TODAY()), MONTH(TODAY()), DAY(TODAY()) - 1) THEN 'Overdue'
  ELSE NULL
END
```

#### 7.Attemp date_task

```
CASE
  WHEN Attemp Date=TODAY() THEN 'Today'
  WHEN Attemp Date>TODAY() THEN 'Overdue'
  ELSE NULL
END
```

#### 8.Followup date_task

```
CASE
  WHEN Followup date=TODAY() THEN 'Pending'
  WHEN Followup date>TODAY() THEN 'Overdue'
  ELSE NULL
END
```

#### 9.Final invoice_task

```
CASE
  WHEN Final invoice="FALSE" and Return date=TODAY() THEN 'Pending'
  WHEN Final invoice="FALSE" and Return date>TODAY() THEN 'Overdue'
  ELSE NULL
END
```
