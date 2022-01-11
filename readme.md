# Book Shop Schema in Postgresql

Create a database schema to hold the information of Authors and Books

## Installation
Install [Postgres & pgAdmin](https://codingpub.dev/ubuntu-install-postgresql-and-pgadmin/) by following the instructions provided.

## Usage

- Download the file "booklist".
- Open pgAdmin4 by providing the correct credentials.
- Right click on the database where you want to import the Schema and it's contents.
- Select Restore.
- Set Format to "Custom or tar"
- Select filename from the path where you downloaded the file "booklist"
- Click on the "Restore" button

OR

 Click on the image below for a step to step guide for Importing file in pgAdmin4
 [![Video Import](https://drive.google.com/uc?export=view&id=1hXZKtk7lhAgi78bS1hF3oCxmshnHNHMu)](https://youtu.be/l5VtQpDl_RA "Video Import")

## Queries

- Find author by name "Leo"

    ```SELECT * FROM authors WHERE name LIKE 'Leo%';```

  
- Find books of author "Fitzgerald"

    ```SELECT * FROM books WHERE author LIKE '%Fitzgerald%';```

        
- Find authors without books

    ```SELECT name FROM authors WHERE name NOT IN (SELECT author FROM books);```

- Count books per country

    ```SELECT country, Count (*) AS Number FROM books INNER JOIN authors ON books.author = authors.name GROUP BY country;```

- Count average book length (in pages) per author

    ```SELECT author,AVG(pages)::numeric(10,2) FROM books GROUP BY author;```


## Questions
- Include potential suggestions on how to improve it.
    
    Following are the ways to improve the provided structure of database
    
    ``` Should have the primary key attribute for both tables ```
    
    ``` Should have an "author_FK" foreign key attribute in the books table rather then the name```
 
 - Consider that there might be millions of authors with millions of books.
 
   ``` Create index on the column ```
   
   ``` Use Pagination : Use Offset and Limit to retrieve portion of records  ```
    
## Tools and Technologies
    
    postgres 12.4

    pdAdmin4
