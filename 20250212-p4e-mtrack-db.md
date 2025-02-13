---
layout: default
---

[Back Home](./index.md)


# Music Track Database with SQLite and Python

Date: 2/12/2025

<br/><br/>
This was a fun assignment put together by the Python For Everyone course on Coursera. It is taught by Charles Russell Severance for the University of Michigan. He is a great teacher (even though he's a Slytherin) and I recommend his courses. I will definitely look at taking other courses of his in the future.

High level overview: use python to create a sqlite database for music tracks that stores several pieces of information for each track in different tables and have those tables link to each other using primary and foreign keys.

This first section of python opens the empty database and creates new tables for Artist, Album, Track, and Genre. For each table, we need to define each column of information.

![db-tables](https://github.com/user-attachments/assets/e0d46904-76ef-46cb-8549-44dec805e87a)


This next section of python opens a csv file with a large number of music tracks exported from a popular music app. The file is then parsed into the different pieces of information that is typically needed for each music track entry. At the same time, primary and foreign keys are designated to form relationships between the different tables. This is done to allow for quick navigation of a database table.
*Note: using an integer key and creating relationships between tables instead of putting all of the actual data in one table speeds up retrieval in large databases. While not necessary in this instance, it is good practice.

![fill-db](https://github.com/user-attachments/assets/dca8114b-662e-4f03-8630-1a3c86b9357e)


The python script was relatively short, but powerful. Here is a snippet of the database using an SQLite browser. You can see the use of foreign keys to match music tracks to their respective album, artist, or genre.

![sqlitedb](https://github.com/user-attachments/assets/f329b29e-e7f1-4399-867c-a4b4d6142d35)


Here is the end product showing a simple join query to visualize how everything comes together.

![joinquery](https://github.com/user-attachments/assets/d6e2ff17-fb9b-4fe4-89fe-2fee79942ac3)


<br/><br/>
[Back Home](./index.md)

