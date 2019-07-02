ElasticSearch
EventDark
Search Engines are hard.
Everyone knows SQL
LEt's not overthink this, people.
Speciality:
Cat Related Events

CREATE TABLE events(
)

SELECT 8 from EVENTS
where start_date > AND start_date < 
AND city = 'Nashville'
AND name = 'Cat';

Results   ..nothing

change from name = 'Cat' to name LIKE '%Cat%'

Results   ..some results


SELECT * FROM Events 
WHERE name LIKE '%cat farming seminar%';

Results didn't match event "Cat Farming Seminar - Dallas"

 Whenever people type it we lowercase it.

Results : event "Cat Farming Seminar - Dallas" matches.


Query 
SELECT * FROM Events 
WHERE lower(name) LIKE '%cat%'
AND lower(name) LIKE '%farming%'
AND lower(name) LIKE '%seminar%';

This query will scan the database 3 times :(

farming and farm doesn't match.

Databases are good at Databasing.
Search Engines are good at Searching.

Particularly Search Engines are good at:
- Finding documents that contain specific terms and phases.
- Scoring and sorting document according to the relevence.
- Filtering/grouping docs aggregating data.

Everything in elasticsearch is a json interface.
Schema : fields that you are going to have.

Filter -> Group -> Aggregate

Index and search 
Content based recommendations are easy to build.
Write only that makes it faster.
k-nearest neighbour is trivially easy.

Explicit mapping in elasticsearch, otherwise everything is a string.
adding analyzer to properties :
We specify that our data to be anazyzed in english.
Analyzed vs Non Analyzed.
 