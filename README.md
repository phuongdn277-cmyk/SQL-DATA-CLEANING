# SQL-DATA-CLEANING
This's a simple exercise for SQL cleaning

## Inspect the initial data:
```sql
SELECT * FROM club_member_clean LIMIT 10;
```
Result:
|full_name|age|martial_status|email|phone|full_address|job_title|membership_date|
|---------|---|--------------|-----|-----|------------|---------|---------------|
|addie lush|40|married|alush0@shutterfly.com|254-389-8708|3226 Eastlawn Pass,Temple,Texas|Assistant Professor|7/31/2013|
|      ROCK CRADICK|46|married|rcradick1@newsvine.com|910-566-2007|4 Harbort Avenue,Fayetteville,North Carolina|Programmer III|5/27/2018|
|Sydel Sharvell|46|divorced|ssharvell2@amazon.co.jp|702-187-8715|4 School Place,Las Vegas,Nevada|Budget/Accounting Analyst I|10/6/2017|
|Constantin de la cruz|35||co3@bloglines.com|402-688-7162|6 Monument Crossing,Omaha,Nebraska|Desktop Support Technician|10/20/2015|
|  Gaylor Redhole|38|married|gredhole4@japanpost.jp|917-394-6001|88 Cherokee Pass,New York City,New York|Legal Assistant|5/29/2019|
|Wanda del mar       |44|single|wkunzel5@slideshare.net|937-467-6942|10864 Buhler Plaza,Hamilton,Ohio|Human Resources Assistant IV|3/24/2015|
|Joann Kenealy|41|married|jkenealy6@bloomberg.com|513-726-9885|733 Hagan Parkway,Cincinnati,Ohio|Accountant IV|4/17/2013|
|   Joete Cudiff|51|divorced|jcudiff7@ycombinator.com|616-617-0965|975 Dwight Plaza,Grand Rapids,Michigan|Research Nurse|11/16/2014|
|mendie alexandrescu|46|single|malexandrescu8@state.gov|504-918-4753|34 Delladonna Terrace,New Orleans,Louisiana|Systems Administrator III|3/12/1921|
| fey kloss|52|married|fkloss9@godaddy.com|808-177-0318|8976 Jackson Park,Honolulu,Hawaii|Chemical Engineer|11/5/2014|

## Data Issues Identified
- Missing and invalid age values 
- Inconsistent letter case
- Leading and trailing whitespaces

## Data cleaning
### Handling inconsistent data
```SQL
UPDATE club_member_clean
SET full_name = TRIM(UPPER(full_name));

UPDATE club_member_clean
SET martial_status = LOWER(TRIM(martial_status));

UPDATE club_member_clean
SET martial_status = 
	CASE
		WHEN martial_status IN ('divored', 'divorced') THEN 'divorced'
		ELSE martial_status
	 END;
```
- Check martial_status column again
```SQL
SELECT DISTINCT martial_status FROM club_member_clean;
```
Resule:
|martial_status|
|--------------|
|married|
|divorced|
||
|single|

### Valid age explanation: 18 – 80, Handing missing and invalid age values
- Check max/ min of Age
``` SQL
SELECT
    MIN(age) AS min_age,
    MAX(age) AS max_age
FROM club_member_clean;
```
- Check count of outlier and null
```SQL
SELECT age, COUNT(*)
FROM club_member_clean
WHERE age IS NULL OR age < 0 OR age > 80
GROUP BY age;
```
- Handing issue
```SQL
UPDATE club_member_clean
SET age = 
	CASE
		WHEN age IS NULL THEN NULL
		WHEN age < 0 THEN NULL
		WHEN age > 80 THEN NULL
		ELSE age
	END;
```
- Check column Age again
```SQL
SELECT age, COUNT(*)
FROM club_member_clean
WHERE age IS NULL OR age < 0 OR age > 80
GROUP BY age;
```
Result:
|age|COUNT(*)|
|---|--------|
||18|

### Handing leading and trailing whitespaces
```SQL
UPDATE club_member_clean
SET
    email           = TRIM(email),
    phone           = TRIM(phone),
    full_address    = TRIM(full_address),
    job_title       = TRIM(job_title),
    membership_date = TRIM(membership_date);
```

## Data Cleaned
```SQL
SELECT * FROM club_member_clean LIMIT 10;
```
Result:
|full_name|age|martial_status|email|phone|full_address|job_title|membership_date|
|---------|---|--------------|-----|-----|------------|---------|---------------|
|ADDIE LUSH|40|married|alush0@shutterfly.com|254-389-8708|3226 Eastlawn Pass,Temple,Texas|Assistant Professor|7/31/2013|
|ROCK CRADICK|46|married|rcradick1@newsvine.com|910-566-2007|4 Harbort Avenue,Fayetteville,North Carolina|Programmer III|5/27/2018|
|SYDEL SHARVELL|46|divorced|ssharvell2@amazon.co.jp|702-187-8715|4 School Place,Las Vegas,Nevada|Budget/Accounting Analyst I|10/6/2017|
|CONSTANTIN DE LA CRUZ|35||co3@bloglines.com|402-688-7162|6 Monument Crossing,Omaha,Nebraska|Desktop Support Technician|10/20/2015|
|GAYLOR REDHOLE|38|married|gredhole4@japanpost.jp|917-394-6001|88 Cherokee Pass,New York City,New York|Legal Assistant|5/29/2019|
|WANDA DEL MAR|44|single|wkunzel5@slideshare.net|937-467-6942|10864 Buhler Plaza,Hamilton,Ohio|Human Resources Assistant IV|3/24/2015|
|JOANN KENEALY|41|married|jkenealy6@bloomberg.com|513-726-9885|733 Hagan Parkway,Cincinnati,Ohio|Accountant IV|4/17/2013|
|JOETE CUDIFF|51|divorced|jcudiff7@ycombinator.com|616-617-0965|975 Dwight Plaza,Grand Rapids,Michigan|Research Nurse|11/16/2014|
|MENDIE ALEXANDRESCU|46|single|malexandrescu8@state.gov|504-918-4753|34 Delladonna Terrace,New Orleans,Louisiana|Systems Administrator III|3/12/1921|
|FEY KLOSS|52|married|fkloss9@godaddy.com|808-177-0318|8976 Jackson Park,Honolulu,Hawaii|Chemical Engineer|11/5/2014|


  




    
  
