-- sum of rows of the 12 tables: 103765+115604+284024+371218+634811+769038+823316+785855+701267+554520+335877+181392=5660687
SELECT COUNT(*)
FROM `BIKE project`.`202201`;

SELECT COUNT(*)
FROM `BIKE project`.`202212`;

-- combine 12 tables
INSERT IGNORE
INTO `BIKE project`.`202212` 
SELECT *
FROM `BIKE project`.`202201`;

INSERT IGNORE
INTO `BIKE project`.`202212` 
SELECT *
FROM `BIKE project`.`202202`;

INSERT IGNORE
INTO `BIKE project`.`202212` 
SELECT *
FROM `BIKE project`.`202203`;

INSERT IGNORE
INTO `BIKE project`.`202212` 
SELECT *
FROM `BIKE project`.`202204`;

INSERT IGNORE
INTO `BIKE project`.`202212` 
SELECT *
FROM `BIKE project`.`202205`;

INSERT IGNORE
INTO `BIKE project`.`202212` 
SELECT *
FROM `BIKE project`.`202206`;

INSERT IGNORE
INTO `BIKE project`.`202212` 
SELECT *
FROM `BIKE project`.`202207`;

INSERT IGNORE
INTO `BIKE project`.`202212` 
SELECT *
FROM `BIKE project`.`202208`;

INSERT IGNORE
INTO `BIKE project`.`202212` 
SELECT *
FROM `BIKE project`.`202209`;

INSERT IGNORE
INTO `BIKE project`.`202212` 
SELECT *
FROM `BIKE project`.`202210`;

INSERT IGNORE
INTO `BIKE project`.`202212` 
SELECT *
FROM `BIKE project`.`202211`;

-- total number of rows
SELECT COUNT(*)
FROM `BIKE project`.`202212` combined;

SELECT *
FROM `BIKE project`.`202212` combined
ORDER BY started_at;

-- rideable_type
SELECT DISTINCT rideable_type
FROM `BIKE project`.`202212` combined;
-- 3 types, electric_bike, classic_bike, docked_bike

-- maximum ride length
SELECT MAX(ride_length) max_ride_length
FROM `BIKE project`.`202212` combined;

-- minimum ride length
SELECT MIN(ride_length) min_ride_length
FROM `BIKE project`.`202212` combined;

-- min_ride_length is ###############################################################################################################################################################################################################################################################
SELECT *
FROM `BIKE project`.`202212` combined
ORDER BY ride_length;
-- ride_id='0793C9208A64302A'; also find out, some ride_length is 00:00:01

DELETE FROM `BIKE project`.`202212` combined
WHERE ride_id='0793C9208A64302A';

-- do not want the rows where the ride_length was shorter than one min
DELETE FROM `BIKE project`.`202212` combined
WHERE ride_length < '00:01:00';

-- see if left ride lengths are >= one minute
SELECT *
FROM `BIKE project`.`202212` combined
ORDER BY ride_length
LIMIT 5000;

-- check NULL values in latitude & longitude
SELECT *
FROM `BIKE project`.`202212` combined
WHERE start_lat IS NULL OR 
start_lng IS NULL OR
end_lat IS NULL OR
end_lng IS NULL;

-- delete those rows
DELETE FROM `BIKE project`.`202212` combined
WHERE start_lat IS NULL OR 
start_lng IS NULL OR
end_lat IS NULL OR
end_lng IS NULL;

-- any start_station_name and end_stattion_name is NULL
SELECT *
FROM `BIKE project`.`202212` combined
WHERE start_station_name IS NULL OR
end_station_name IS NULL;

-- delete these rows as well 
DELETE FROM `BIKE project`.`202212` combined
WHERE start_station_name IS NULL OR
end_station_name IS NULL;

SELECT *
FROM `BIKE project`.`202212` combined
ORDER BY start_station_name
LIMIT 300;

-- number of rows now: 4293609
SELECT COUNT(*)
FROM `BIKE project`.`202212` combined;

-- number of casual riders and Cyclistic members
SELECT member_casual, COUNT(member_casual) AS amount
FROM `BIKE project`.`202212` combined
GROUP BY member_casual;
-- Tableau#1

-- average ride length
SELECT AVG(ride_length) AS avg_ride_length
FROM `BIKE project`.`202212` combined;

--  average ride length for casual riders and members 
SELECT member_casual, AVG(ride_length) AS avg_ride_length
FROM `BIKE project`.`202212` combined
GROUP BY member_casual;

-- average ride length by bike type
SELECT rideable_type, AVG(ride_length) AS avg_ride_length
FROM `BIKE project`.`202212` combined
GROUP BY rideable_type;

UPDATE `BIKE project`.`202212` combined
SET  
	day_of_week = 
            CASE
                WHEN day_of_week = '1' THEN 'Sunday'
                WHEN day_of_week = '2' THEN 'Monday'
                WHEN day_of_week = '3' THEN 'Tuesday'
                WHEN day_of_week = '4' THEN 'Wednesday'
                WHEN day_of_week = '5' THEN 'Thursday'
                WHEN day_of_week = '6' THEN 'Friday'
                WHEN day_of_week = '7' THEN 'Saturday' 
            END
WHERE
        day_of_week IN ('1', '2', '3', '4', '5', '6', '7');

-- total rides by day	
SELECT member_casual, day_of_week, COUNT(ride_id) AS rides
FROM `BIKE project`.`202212` combined
GROUP BY member_casual, day_of_week
ORDER BY day_of_week;

-- total bike rides by bike type 
SELECT member_casual, rideable_type, COUNT(ride_id) AS rides
FROM `BIKE project`.`202212` combined
GROUP BY member_casual, rideable_type;

-- total bike rides monthly
SELECT member_casual, started_at, Count(ride_id) AS total_rides
FROM `BIKE project`.`202212` combined
GROUP BY member_casual, started_at
ORDER BY started_at;

-- Top 5 starting stations by casual riders
SELECT start_station_name, member_casual, start_lat, start_lng, COUNT(ride_id) AS rides_started_here
FROM `BIKE project`.`202212` combined
WHERE member_casual= 'casual'
GROUP BY start_station_name, member_casual, start_lat, start_lng
ORDER BY rides_started_here DESC
LIMIT 5;

-- Top 5 starting stations by members
SELECT start_station_name, member_casual, start_lat, start_lng, COUNT(ride_id) AS rides_started_here
FROM `BIKE project`.`202212` combined
WHERE member_casual= 'member'
GROUP BY start_station_name, member_casual, start_lat, start_lng
ORDER BY rides_started_here DESC
LIMIT 5;

-- Top 5 ending stations by members
SELECT end_station_name, member_casual, end_lat, end_lng, COUNT(ride_id) AS rides_ended_here
FROM `BIKE project`.`202212` combined
WHERE member_casual= 'member'
GROUP BY end_station_name, member_casual, end_lat, end_lng
ORDER BY rides_ended_here DESC
LIMIT 5;

-- Top 5 ending stations by casual riders
SELECT end_station_name, member_casual, end_lat, end_lng, COUNT(ride_id) AS rides_ended_here
FROM `BIKE project`.`202212` combined
WHERE member_casual= 'casual'
GROUP BY end_station_name, member_casual, end_lat, end_lng
ORDER BY rides_ended_here DESC
LIMIT 5;
