[[home]](../../../../home.html) 

> **Play framework**

[oficial site](https://www.playframework.com/)<br/>
[oficial documentation](https://www.playframework.com/documentation/2.3.x/Home)
 

- [Definition](#definition)
- [Tutorials](#tutorials)
- [Details](#details)
- [Installing Play](#play_install)


<a name="definition"></a>
> **Definition:** <br/>

<a name="tutorials"></a>
> **Tutorials:** <br/>

  
<a name="details"></a>
> **Details:**<br/>

<a name="play_install"></a>
> **Installing Play:** 

- **Install Activator** (Play is distributed through Typesafe Activator tool. Typesafe Activator provides the build tool (sbt) that Play is built on, and also provides many templates and tutorials to help get you started with writing new applications) [(more)](https://www.playframework.com/documentation/2.3.x/Installing)

		# check the activator help 
		$ activator -help

		# in the project folder, runs Activator UI 
		$ activator ui

> **Create new application with Activator** (The activator command can be used to create a new Play application. Activator allows you to select a template that your new application should be based off) [(more)](https://www.playframework.com/documentation/2.3.x/NewApplication)

		# to create a new vanilla Play Scala application
		$ activator new app-name play-scala

		# to create a new vanilla Play Java application
		$ activator new app-name play-java

> **Create new application without Activator** (It is also possible to create a new Play application without installing Activator, using sbt directly)

- install sbt [(download)](http://www.scala-sbt.org/)
- configure project/plugins.sbt and project/build.properties [(more)](https://www.playframework.com/documentation/2.3.x/NewApplication)

> **Using the Play console** (The Play console is a development console based on sbt that allows you to manage a Play application’s complete development cycle)[(more)](https://www.playframework.com/documentation/2.3.x/PlayConsole)

	# launching the console
	> cd app-folder
	> activator
	
	# getting help
	# shows available commands
	$ help
	# using with specific command to get info about 
	$ help run

	# run server in development mode
	$ run

	# to stop the server
	Crtl+D key

	# compile your application without running the server
	$ compile

	# starts JPDA debug port
	$ activator -jvm-debug <port> 
	  

> **Get key-value properties** [(more)](http://alvinalexander.com/scala/play-framework-how-read-application-conf-properties-settings)

	# add key-value property to application.conf configuration properties
	play.Play.application.configuration.getString("prop.key")

> **Job tasks**

	# set job task class in the application.conf for property
	 application.global=controllers.JobTaskController 
 
	# create class for ex: JobTaskController that extends GlobalSettings
	# overridde onStart(Application app) method
	Akka.system().scheduler().schedule(
        Duration.create(0, TimeUnit.MILLISECONDS),
        Duration.create(5, TimeUnit.MINUTES),
            new Runnable() {
            	public void run() {
                    // TODO: code for execution 
                }
            },
            Akka.system().dispatcher()
    ); 
 
- Other scheduler example  [here](http://doc.akka.io/docs/akka/2.0/java/scheduler.html)

