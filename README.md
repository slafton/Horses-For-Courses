# Horses-For-Courses

## Purpose
Using the horses for courses data, analyze differences based on gender of racehorse.

## ETL
* CSV's were read into JupyterNotebook for initial analysis. An ERD was then created.

![schema](https://github.com/slafton/Horses-For-Courses/blob/main/Images/QuickDBD-export%20(1).png)

* Tables were then created in PgAdmin. 

![new_runners](https://github.com/slafton/Horses-For-Courses/blob/main/Images/new_runnersTable.png)

![horses](https://github.com/slafton/Horses-For-Courses/blob/main/Images/horsesTable.png)

![horse_sexes](https://github.com/slafton/Horses-For-Courses/blob/main/Images/horsesSexesTable.png)

* The id column in the horse_sexes table was renamed sex_id

ALTER TABLE horse_sexes
RENAME COLUMN id TO sex_id;

![horse_sexes_new](https://github.com/slafton/Horses-For-Courses/blob/main/Images/new_runnersTable.png)

* A new table was created and exported as a CSV.

SELECT horses.id, horses.age, horses.sex_id, horses.sire_id, horses.dam_id, horses.prize_money, new_runners.handicap_weight
INTO new_horses
FROM horses
JOIN new_runners ON horses.id = new_runners.id;

![new_horses](https://github.com/slafton/Horses-For-Courses/blob/main/Images/new_runners%20joined%20with%20horses.png)

## Results

Results of queries by gender with counts per gender:

* Geldings

![Gelding Query](https://github.com/slafton/Horses-For-Courses/blob/main/Images/geldingquery.png)

![Gelding Count](https://github.com/slafton/Horses-For-Courses/blob/main/Images/countofGeldings.png)

* Fillies

![Filly Query](https://github.com/slafton/Horses-For-Courses/blob/main/Images/fillyquery.png)

![Filly Count](https://github.com/slafton/Horses-For-Courses/blob/main/Images/countofFillies.png)

* Mares

![Mare Query](https://github.com/slafton/Horses-For-Courses/blob/main/Images/marequery.png)

![Mare Count](https://github.com/slafton/Horses-For-Courses/blob/main/Images/countofMares.png)

* Colts

![Colt Query](https://github.com/slafton/Horses-For-Courses/blob/main/Images/Coltquery.png)

![Colt Count](https://github.com/slafton/Horses-For-Courses/blob/main/Images/countofColts.png)

* Unknowns

![Unknown Query](https://github.com/slafton/Horses-For-Courses/blob/main/Images/Unknownqueryandcount.png)

* Horses

![Horse Query](https://github.com/slafton/Horses-For-Courses/blob/main/Images/horsequery.png)

![Horse Count](https://github.com/slafton/Horses-For-Courses/blob/main/Images/horsequery.png)

## Summary

![Race Horse Gender Analysis in Tableau](https://public.tableau.com/app/profile/afton.snider/viz/RacehorseAnalysisbyGender/RacehorseAnalysisbyGender?publish=yes)

* Average Age by Sex

![image](https://github.com/slafton/Horses-For-Courses/blob/main/Images/AverageAgebySex.png)

The average age for geldings and mares is very close as is the average age for colts and fillies.

* Handicap Weights by Gender

![image](https://github.com/slafton/Horses-For-Courses/blob/main/Images/HandicapWeightsByGender.png)

Handicap weights are similar for all genders. We can see that mares had the highest outlier (72.50) followed by geldings and colts (70.50).

* Median Prize Money by Gender

![image](https://github.com/slafton/Horses-For-Courses/blob/main/Images/HandicapWeightsByGender.png)

Geldings and colts had higher average winnings than mares and fillies. Geldings average winnings were $5,587 more than mares and colts average winnings were $1,320 more than fillies.

