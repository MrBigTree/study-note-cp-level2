## Oracle Users
### two types of users
- admin user:
  - SYS
  - SYSTEM
- developer user (HR, developer)

### Create user and connect as a user
- how to create a user and give it required permissions?
  - must login as sys: sys as sysdba
  - create user: 
  CREATE USER ethanli
  IDENTIFIED BY avangers  // whatever followed by IDENTIFIED BY is the password
  QUOTA unlimited ON USERS;
- select username from dba_users // check users
- connect ethanli/avangers // connect as user "ethanli" with password "avangers"

### Oracle Privileges & Roles
- Privileges 
  - System Privileges - can be granted only by the DBA (i.e
  . SYS user)
  - Object Privileges - can be granted by the owner or DBA;
- grant previleges to users
  - SQL>GRANT connect, resource TO ethanli
  - SQL>REVOKE connect, resource TO ethanli
- SYS can create multiple DBA, DBA is 24*7 job and common have multiple DBA work on shifts.

## Database Objects
- Physical database objects
- logical database objects


SQL> desc table_name 

SET SERVEROUTPUT ON // by default no output shown in cmd

ed // open the last sql script you inputed

:= // assign a variable in pl/sql


trigger: timing, event, object

run cmd as admin so you can see the texteditor 


/
show error

desc my_pack