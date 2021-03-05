http://www.seanlahman.com/baseball-archive/statistics/
1. Find the players who made it into the hall of fame who played for a college located in NY return the player ID, first name, last name, and school ID. Group the players by School.
2. Create a Table of all players with a first name of John who were born in the United States and played at Fordham university.
Include their first name, last name, playerID, and birth state.



1)	SELECT Schools.schoolID,first(People.playerID),first(People.nameFirst),first(People.nameLast)
	FROM HallOfFame 
	INNER JOIN People ON HallOfFame.playerID = People.playerID
	INNER JOIN CollegePlaying ON HallOfFame.playerID = CollegePlaying.playerID
	INNER JOIN Schools ON CollegePlaying.schoolID=Schools.schoolID
	WHERE Schools.schoolCity="NY" 
	GROUP BY Schools.schoolID

2)	CREATE TABLE PLAYERS_JOHN AS
		SELECT People.nameFirst, People.nameLast, People.playerID, People.birthState
		FROM People 
		INNER JOIN CollegePlaying ON People.playerID = CollegePlaying.playerID
		INNER JOIN Schools ON CollegePlaying.schoolID=Schools.schoolID
		WHERE People.nameFirst="John" AND People.birthCountry="United States" AND Schools.schoolName="Fordham university"