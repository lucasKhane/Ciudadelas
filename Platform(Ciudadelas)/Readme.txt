La idea: crear la plataforma lo mas sencilla posible con Meteor.
Iré apuntando alguna cosa que me parezca interesante y que vaya aprendiendo.

Cuaderno de bitacora:
https://www.meteor.com/tutorials/blaze/creating-an-app
http://docs.meteor.com/#/basic/quickstart

Create a project:
	meteor create myapp
Run it locally:
	cd myapp
	meteor
	# Meteor server running on: http://localhost:3000/
Then, open a new terminal tab and unleash it on the world (on a free server we provide):
	meteor deploy myapp.meteor.com
#Que majos, nos dejan un servidor. Fantastico.

Command Line Tool
meteor help
meteor create <name>
	Make a subdirectory called <name> and create a new Meteor app there.
meteor run
	Serve the current app at http://localhost:3000 using Meteor's local development server.
meteor debug
	Run the project with Node Inspector attached, so that you can step through your server code line by line. See meteor debug in the full docs for more information.
meteor deploy <site>
	Bundle your app and deploy it to <site>. Meteor provides free hosting if you deploy to <your app>.meteor.com as long as <your app> is a name that has not been claimed by someone else.
meteor update
	Update your Meteor installation to the latest released version and then (if meteor update was run from an app directory) update the packages used by the current app to the latest versions that are compatible with all other packages used by the app.
meteor add
	Add a package (or multiple packages) to your Meteor project. To query for available packages, use the meteor search command.
meteor remove
	Remove a package previously added to your Meteor project. For a list of the packages that your application is currently using, use the meteor list command.
meteor mongo
	Opens a MongoDB shell for viewing and/or manipulating collections stored in the database. Note that you must already be running a server for the current app (in another terminal window) in order for meteor mongo to connect to the app's database.
meteor reset
	Reset the current project to a fresh state. Removes all local data.
	If you use meteor reset often, but you have some initial data that you don't want to discard, consider using Meteor.startup to recreate that data the first time the server starts up:

if (Meteor.isServer) {
  Meteor.startup(function () {
    if (Rooms.find().count() === 0) {
      Rooms.insert({name: "Initial room"});
    }
  });
}

#Empecemos con el tutorial, a ver si recuerdo como iba esto:
1.- TEMPLATES
JS:
if (Meteor.isClient) {
  // This code only runs on the client
  Template.body.helpers({
    tasks: [
      { text: "This is task 1" },
      { text: "This is task 2" },
      { text: "This is task 3" }
    ]
  });
}

HTML:
<head>
  <title>Todo List</title>
</head>

<body>
  <div class="container">
    <header>
      <h1>Todo List</h1>
    </header>
    <ul>
      {{#each tasks}}
        {{> task}}
      {{/each}}
    </ul>
  </div>
</body>

<template name="task">
  <li>{{text}}</li>
</template>

CSS: en general

2.- COLLECTIONS
Básicamente colecciones con la base de datos MongoDB

3.-FORMS AND EVENTS
Esto recuerdo que tenía su aquel...sobre todo jugando con las propiedades de los formularios

4.- UPDATE AND REMOVE
Interesante. No me acordaba, pero vamos, trivial

5.- DEPLOYING OUT APP
Simply go to your app directory, and type:

meteor deploy my_app_name.meteor.com

Once you answer all of the prompts and the upload completes, you can go to http://my_app_name.meteor.com and use your app from anywhere. 


6.- RUNNING ON MOBILE
Esto es interesante. No sabía que se podía correr en android o bajo emuladores iOS. Pero de momento no me interesa.

7.- TEMPORARY UI STATE
Bueno, utiliza el estado de la sesión

8.- ADDING USER ACCOUNTS
Cuentas de usuario...
To enable the accounts system and UI, we need to add the relevant packages. In your app directory, run the following command:

meteor add accounts-ui accounts-password

Ojo con las cosas en las que necesitas añadir archivitos. Esto lo dejo ya hecho, aunque de momento no me haga falta.

Hay varos tipos de paquetes de usuario que se pueden añadir. Por ejemplo accounts-facebook. 

9.- SECURITY WITH METHODS
Removing insecure

Every newly created Meteor project has the insecure package added by default. This is the package that allows us to edit the database from the client. It's useful when prototyping, but now we are taking off the training wheels. To remove this package, go to your app directory and run:

meteor remove insecure

Lo dejamos ya así, que como no somos tontos, seguro que lo hacemos fantásticamente.

Solo cuidado porque si coges codigo de tu otra plataforma, puede que te pidas cosas como estar registrado y cosas así. Bueno, y que necesitas llamar a metodos para acceder a algunas cosas. Lo vas mirando.

10.- PUBLISH AND SUBSCRIBE

Just like with insecure in the last step, all new Meteor apps start with the autopublish package. Let's remove it and see what happens:

meteor remove autopublish

When the app refreshes, the task list will be empty. Without the autopublish package, we will have to specify explicitly what the server sends to the client. The functions in Meteor that do this are Meteor.publish and Meteor.subscribe.

Esto de la seguridad es lo que menos caña le di en su dia. Acabo de ver que hay metodos para hacer cosas privadas o parcialmente privadas.
En algun momento tendre que revisarlo, pero no es el dia.

11.- NEXT STEPS
Guia completa : http://guide.meteor.com/
Documentacion: http://docs.meteor.com/#/basic/
Herramientas: https://www.meteor.com/tools
Y recursos: https://www.meteor.com/tools/resources
Para integrar en la aplicaciones en las que use Meteor

EMPEZANDO:
0.- Si faltan letras en la documentación, concretamente la "e", la "f", o la "g", es que el teclado a veces se las come. El pobre hace lo que puede
1.- Voy simplemente a dejar un botoncete de inicia algo, aunqu hay cosas que mereza la pena recuperar, como los crear partida, las salas de espera y etc etc.


