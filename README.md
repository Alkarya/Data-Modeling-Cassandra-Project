# Project - Data Modeling Apache Cassandra

## Project Description

This project has to purpose to support a startup called Sparkify that needs to analyze their data. 
This data is related to the songs and the users activity on their app. 
In this case the analysis team is interested in understanding what songs their users are listening.
This data resides in a CSV file and it is needed to create a process to extract, tranform and load the data into a Apache cassandra database

## Repo Structure

* `/event_data` - data source used to feed the database
* `/images` - resources needed for the project
* `/notebooks`- notebooks used for this project

### Notebooks
* `Project_1B_Project_Template.ipynb` - notebok used to create the tables and load the data

## Tables 

### Query 1

Table used to answer the first question

1. **song_by_session** - Table created to find the artist, song title and song length, by filtering using the sessionId and ItemInSession
   * sessionId, itemInSession, artist, song, length
   * PRIMARY KEY(sessionId, itemInSession)

### Query 2

Table used to answer the second question

2. **song_by_user** - Table created to find the name of artist, song (sorted by itemInSession) and user (first and last name) by filtering using the userid and sessionid.
   * user_id, sessionId, itemInSession, artist, song, firstName, lastName
   * PRIMARY KEY ((userId, sessionId), itemInSession)

### Query 3

Table used to answer the third question

3. **user_by_song** - Table created to find the name of userId, firstName and lastName of a user that listen to a specific song
   * song, firstName, lastName, userId
   * PRIMARY KEY (song, firstName, lastName, userId)


## How to run locally

1. Clone repo and change diretory

```bash
git clone https://github.com/Alkarya/Data-Modeling-Cassandra-Project.git

cd data-modeling-cassandra-project
```
2. Start postgres docker image

```bach
docker-compose up
```

3. Create Python venv

On a new terminal run:
```bash
python3 -m venv python-venv            
source python-venv/bin/activate 
```

4. Install requisits

```bash
pip install -r requirements.txt
```

5. Launch Jupyter Notebooks

```bash
cd notebooks
jupyter lab
```
This should open on the browser jupyter notebooks

6. Closing and cleaning the local environment

Press `cntr + c` in the terminal to close jupyter notebooks

```bash
cd ..
deactivate
rm -r python-venv
```
On the other terminal press `cntr + c` to close docker

```bash
docker kill
docker system prune -a
docker network prune
```

## References

* Set up [Cassandra Docker Compose](https://cloudinfrastructureservices.co.uk/how-to-setup-cassandra-docker-container-using-docker-compose/) 
* [Cassandra Keys](https://www.baeldung.com/cassandra-keys)
  

