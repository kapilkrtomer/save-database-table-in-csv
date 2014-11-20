save-database-table-in-csv
==========================


import csv
import MySQLdb

def main():
    db = MySQLdb.connect("localhost","root","6Tresxcvbhy")
    cursor = db.cursor()

    #sql = """ create database IF NOT EXISTS  zivame """
    #cursor.execute(sql)

    sql =""" use funglee """
    cursor.execute(sql)

   #cursor = connection.cursor() # assuming you know how to connect to your oracle db
    cursor.execute(""" select * from  junglee_class_seller_data """)
    with open('junleet2.csv', 'wb') as fout:
        writer = csv.writer(fout)
        writer.writerow([ '"%s"' %(i[0]) for i in cursor.description ]) # heading row
        writer.writerows(cursor.fetchall())

if __name__ =="__main__":
    main()
