Linux commands:
1. sudo apt update
2. sudo apt install postgresql postgresql-contrib
3. sudo systemctl start postgresql.service
4. service postgresql status
5. sudo -u postgres psql - run postgresql as postgres user OR sudo -u -i postgres - interactive session
6. sudo -u postgres createuser --interactive - create user as postgres
7. #if YOU WANT TO CREATE A USER FOR DATABASE DO NOT FORGET TO CREATE MATCHING DATABASE FIRST

Other Linux:
sudo apt-get install openssh-server
sudo systemctl start/enable ssh
kill -<signal_number> <PID>
pgrep "process" - get the pid of the process
ps -p 123 - get info of the PID 123

Postgree commands:
\l - check avaiable databases
\q - quit postgresql
exit - quit from postgres interactive session
psql -d "database" - switch database

SQL:
CREATE DATABASE 



try:
    with SSHTunnelForwarder(
         ('some.linktodb.com', 22), # port 22 as standard SSH port
        ssh_username="username", 
        ssh_pkey="your/private/key", # your private key file
        ssh_private_key_password="****",
        remote_bind_address=('localhost', 5432)) as server: # mirroring to local port 5432
         
         server.start()

         params = { # database params
             'database': 'test',
             'user': 'dome',
             'password': '*****',
             'host': 'localhost',
             'port': server.local_bind_port
             }
         conn = psycopg2.connect(**params)
         curs = conn.cursor() # if this works, you are connected
         print("DB connected")
except:
    print("Connection failed")
