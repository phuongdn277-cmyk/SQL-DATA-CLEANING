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
    ```SQL
    SELECT * FROM club_member_clean cmc 
    WHERE age < 0 OR age > 100 OR age IS NULL;
    ```
    Result:
|full_name|age|martial_status|email|phone|full_address|job_title|membership_date|
|---------|---|--------------|-----|-----|------------|---------|---------------|
|Jori Sanz|399|married|jsanz3i@google.cn|904-906-7537|99 West Crossing,Jacksonville,Florida|Professor|2/15/2012|
|Carlye Graeber|555|married|cgraeber6n@quantcast.com|214-345-1363|8 Dexter Junction,Dallas,Texas|Actuary|3/10/2021|
|Shurwood Strutley|544|married|sstrutley9w@craigslist.org|804-636-0234|7779 Main Road,Richmond,Virginia|Nuclear Power Engineer|6/30/2014|
|Corbin Hillan|499|single|chillandg@time.com|267-229-4017|78 La Follette Trail,Philadelphia,Pennsylvania|Account Representative II|7/7/2021|
|Smitty Bulmer|522|divorced|sbulmergm@addthis.com||23370 Forest Dale Street,Pittsburgh,Pennsylvania|VP Marketing|9/25/2017|
|Leonore BoothJarvis||married|lboothjarvisi2@bloglines.com|713-618-0516|33110 Luster Plaza,Houston,Texas|Sales Representative|6/13/2022|
|Aundrea Villar|277|married|avillarm8@privacy.gov.au|571-942-0462|58201 Utah Terrace,Arlington,Virginia|Senior Sales Associate|6/28/2012|
|Chery Batisse||divorced|cbatissen3@bandcamp.com|804-431-7226|604 Elgar Way,Richmond,Virginia|VP Product Management|7/30/2012|
|erina aubert|288|married|eaubertqp@cargocollective.com|615-711-2470|2597 Hallows Road,Nashville,Tennessee|Automation Specialist II|11/2/2012|
|Baldwin Rippen|588|single|brippen1z@nationalgeographic.com|912-469-5562|2 Esker Alley,Savannah,Georgia|Web Developer II|12/1/2015|
|Cherise Kristoffersson|599|divorced|ckristoffersson59@sun.com|806-779-9348|72793 Northridge Park,Lubbock,Texas|Director of Sales|8/2/2021|
|thorndike portingale|677|married|tportingale9n@nsw.gov.au|941-186-3805|9011 Huxley Plaza,Sarasota,Florida|Statistician II|2/16/2019|
|Haskell Braden|322|divorced|hbradenri@freewebs.com|510-963-9848|35005 Waubesa Crossing,Berkeley,California|Dental Hygienist|11/4/2015|
|Montague Latham|644|married|mlathame5@dailymotion.com|210-522-8041|0 Buhler Plaza,San Antonio,Texas|Administrative Officer|2/13/2021|
|Virgina Hubbock||single|vhubbockep@ed.gov|540-535-0069|7 Schmedeman Center,Roanoke,Virginia|Media Manager I|7/6/2021|
|Alva Dell 'Orto|411|married|adellhp@yale.edu|951-142-9340|10 Carpenter Lane,Riverside,California|Food Chemist|3/10/2019|
|denni stallard|633|single|dstallardl9@devhub.com|816-567-5883|73737 Kinsman Street,Saint Joseph,Missouri|Nuclear Power Engineer|7/3/2018|
|Cathrine Jonson|222|married|cjonsonol@aboutads.info|559-318-4841|4147 Swallow Hill,Fresno,California|Speech Pathologist|4/26/2022|


    
  
