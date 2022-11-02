"C:\Program Files\MongoDB\Server\6.0\bin\mongod.exe" 
--config "C:\Program Files\MongoDB\Server\6.0\bin\mongod.cfg" --service


sc.exe create MongoDB-Auth binPath="\"C:\Program Files\MongoDB\Server\6.0\bin\mongod.exe\" –service config=\"C:\Program Files\MongoDB\Server\6.0\bin\mongod_auth.cfg\"" DisplayName= "MongoDB-Auth" start="auto"

SC STOP shortservicename
SC DELETE shortservicename

Also:
sc delete "MongoDB-Auth"



https://www.mongodb.com/docs/manual/tutorial/configure-scram-client-authentication/#std-label-scram-client-authentication


db.createUser({ user: "myUserAdmin", pwd: "Hello1234", 
roles: [
  { role: "userAdminAnyDatabase", db: "admin" },
  { role: "readWriteAnyDatabase", db: "admin" }
]
})


Source:
https://stackoverflow.com/questions/56110254/how-to-run-mongodb-as-a-service-with-authentication-on-a-windows-machine

### Bash-Terminal
cd '/c/Program Files/MongoDB/Server/6.0/bin/'
mv mongod_auth.cfg mongod.cfg

### DataGrip-Console

show databases
use config

use admin
show collections

use mflix
db.users.find()


db.createUser(
  {
    user: "myUserAdmin",
    pwd: "Hello1234",
    roles: [
      { role: "userAdminAnyDatabase", db: "admin" },
      { role: "readWriteAnyDatabase", db: "admin" }
    ]
  }
)

use admin
db.system.users.find()


use mflix
show collections

//https://www.mongodb.com/docs/manual/reference/built-in-roles/#std-label-built-in-roles
db.createUser(
   {
     user: "mflixAdmin1",
     pwd: "Hello1234",  // Or  passwordPrompt()
     roles: [ "readWrite", "dbAdmin" ]
   }
)