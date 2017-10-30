# National Parks

## Build the application (Mac)

Install Maven and Tomcat. I am assuming that java is already installed with these tools.

```
$ brew install maven
$ brew install tomcat
```

## Populate the database

Add all the national parks data to the mongo database

```
$ mongoimport --drop -d demo -c nationalparks --type json --jsonArray --file ./national-parks.json $*
```

## Run the application (Mac)

Copy the built war into tomcat's war directory.

```
$ cp target/national-parks.war $(catalina -h | grep CATALINA_HOME | cut -d ' ' -f 5)/webapps
$ catalina run
```

Visit http://localhost:8080/national-parks
