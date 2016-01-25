IA.js
-Contiene la lógica del juego
-Datos iniciales de fichas y demás
-Funciones de que cosas hacen las fichas
-Como funciona el mazo, y sus funciones que lo gestionan
-Como funciona el tablero y la interacción con él
-Lógica de la partida y datos iniciales
-Gestión de los jugadores

IU.js
-Aquí en principio pero debo mejorarlo, somos llamados por la IA para
empezar la partida.
-Básicamente empieza partidas y las prepara para dejarlas registradas. Como
Por ahora simplemente quiero que el juego funcione para mí, no creo que sea
muy necesario.

servidor.js
-Gestión de la interfaz de usuario desde el punto de vista del servidor:
llamadas a mongo, metodos, .allow para gestionar la privacidad del subscribe,
y los publish. Cuentas de usuario y cosas así.
