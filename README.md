# Assessment_VEngage.AI

## Problem 1:
Write a method that reads phone book records from a CSV or JSON file.
Each record consists of the following parameters Name, email, Phone 1, Phone 2.

First I create a csv file that is mention in problem 1 statment. I have imported few libraries because we will open csv file and stored in one variable. 

                                    import csv
                                    
we need connection between sql and python. so below mention libraries used to connect                                  
                                    
                                    

                       !pip install pymysql
                       !pip install mysql-connector-python
                       import sqlalchemy
                       import pymysql
                       from sqlalchemy import create_engine
                       from sqlalchemy import text
                       from sqlalchemy import create_engine, text 
                       import mysql.connector as sql
                       
we want to create a database                       

                       mycursor.execute("CREATE DATABASE phonebook_records")

we want to create a table because we insert data. 

                       create_table_query = """
                                         CREATE TABLE phone_records (
                                                   Name VARCHAR(255),
                                                   email VARCHAR(255),
                                                   Phone_1 VARCHAR(15),
                                                   Phone_2 VARCHAR(15)
                                                  )
                                                  """                                     
                               mycursor.execute(create_table_query)

We  extracted data from csv that extracted data is stored in mysql database using below mentioned coding
                          
                          for data in phone_book_records:
                                name=data["Name"]
                                Email=data['Email']
                                Phone_1=data['Phone 1']
                                Phone_2=data['Phone 2']
                    
                      insert_query = f"""
                           INSERT INTO phone_records (Name, email, Phone_1, Phone_2)
                            VALUES ('{name}', '{Email}', '{Phone_1}', '{Phone_2}')
                                """
                         mycursor.execute(insert_query)
                         mydb.commit()
                        print("\n Inserted successfully")
# Problem 2:
Implement a SQL-like parser for phone book records in Problem 1 to implement CRUD 
operaNons and print SQL like output on console.

SELECT * FROM phone_records; This statement reads the first 10 records and displays them 
on the console.

SELECT * FROM phone_records WHERE name=’doe’; this statement filters the records and 
displays the record(s) where ‘Doe’ is found

INSERT INTO phone_records(name, email,phone 1, phone 2) 
VALUES(‘Test’,’test@test.xtyz’,’1234456’,’1233233’)
This statement should create a new entry in the dataset and the same should be obtained 
when execuNng secNon 2.2 (i.e. the previous example)

DELETE FROM phone_records WHERE name=’John’
This statement should delete the record from the dataset

The above mention problem 2 statement exact solution code is below mentioned
                           select_all_query = "SELECT * FROM phone_records LIMIT 10"
                           mycursor.execute(select_all_query)
                           result_select_all = mycursor.fetchall()
                           print("2.1 - SELECT * FROM phone_records limit 10:")
                           print(result_select_all)

# 2.2 SELECT * FROM phone_records WHERE name='Doe'; (filters records where 'Doe' is found)
                   select_doe_query = "SELECT * FROM phone_records WHERE name='Doe'"
                   mycursor.execute(select_doe_query)
                   result_select_doe = mycursor.fetchall()
                   print("\n2.2 - SELECT * FROM phone_records WHERE name='Doe':")
                   print(result_select_doe)

# 2.3 INSERT INTO phone_records(name, email, phone_1, phone_2) VALUES('Test', 'test@test.xtyz', '1234456', '1233233')
                    insert_query = """
                    INSERT INTO phone_records (Name, email, Phone_1, Phone_2)
                    VALUES ('Test', 'test@test.xtyz', '1234456', '1233233')
                    """
                    mycursor.execute(insert_query)
                    mydb.commit()
                    print("\n2.3 - INSERT INTO phone_records: Record inserted successfully.")
                   select_test_query = "SELECT * FROM phone_records WHERE name='Test'"
                   mycursor.execute(select_test_query)
                   result_select_test = mycursor.fetchall()
                   print("2.3 - SELECT * FROM phone_records WHERE name='Test':")
                   print(result_select_test)

# 2.4 DELETE FROM phone_records WHERE name='John'; (deletes the record where name is 'John')
                 delete_query = "DELETE FROM phone_records WHERE name='Jhon'"
                 mycursor.execute(delete_query)
                 mydb.commit()
                print("\n2.4 - DELETE FROM phone_records: Record deleted successfully.")
                select_check_query = "SELECT * FROM phone_records WHERE name='Jhon'"
                mycursor.execute(select_check_query)
                result_select_check = mycursor.fetchall()
                print("\n2.4 - SELECT * FROM phone_records WHERE name='Jhon':")
                print(result_select_check)


                        

                               
