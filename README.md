# PongGame

To make a Pong game in Java using the Java Swing library, we create 6 different classes:

PongGame: This class would be the main class that runs the game and sets up the GameFrame, GamePanel, Paddles, Ball, and Scores.

GameFrame: This class would extend JFrame and create the window for the game. It would also add the GamePanel to the frame.

GamePanel: This class would extend JPanel and would be responsible for drawing the game elements (paddles, ball, and scores) on the screen.

Paddles: This class would represent the paddles in the game and would have properties such as position, size, and movement.

Ball: This class would represent the ball in the game and would have properties such as position, size, and movement.

Scores: This class would keep track of the scores for each player and would have methods for updating and displaying the scores on the screen.

These classes would interact with each other to create the Pong game. The GamePanel would use the Paddles and Ball classes to draw the game elements on the screen, and the PongGame class would use the GameFrame and GamePanel classes to set up and run the game.




##GamePanel.java 
 javax.swing package, which contains classes for creating graphical user interface (GUI) components such as buttons, labels, and panels.
 java.awt package, which contains classes for creating and manipulating graphical elements such as colors, fonts, and layouts.
 java.awt.event package, which contains classes for handling events in a GUI such as key presses and mouse clicks.
 java.util package, which contains the Random class used to generate random numbers.
The fifth line declares the GamePanel class, which extends the JPanel class, which is a basic container for GUI components. It also implements the Runnable interface which allows the class to be executed as a separate thread.
The sixth line creates a constant variable named GAME_WIDTH and assigns the value of 1000 to it.
The seventh line creates a constant variable named GAME_HEIGHT and assigns the value of (GAME_WIDTH*(0.555)) to it.
The eight line creates a constant variable named SCREEN_SIZE, which is of type Dimension, and assigns the value of a new Dimension object with the values of GAME_WIDTH and GAME_HEIGHT.
The ninth line creates a constant variable named PADDLE_HEIGHT and assigns the value of 100 to it.
The tenth line creates a constant variable named PADDLE_WIDTH and assigns the value of 25 to it.
The eleventh line creates a constant variable named BALL_DIAMETRE and assigns the value of 20 to it.
The twelfth line creates a variable named gameThread of type Thread.
The thirteenth line creates a variable named image of type Image.
The fourteenth line creates a variable named graphics of type Graphics.
The fifteenth line creates an object of Paddles class and assigns to variable named paddle1.
The sixteenth line creates an object of Paddles class and assigns to variable named paddle2.
The seventeenth line creates an object of Ball class and assigns to variable named ball.
The eighteenth line creates an object of Scores class and assigns to variable named score, it also passed the GAME_WIDTH and GAME_HEIGHT as parameter.

## GamePanel() - constructor of the GamePanel class
The first line defines the constructor of the GamePanel class. It is called when an object of the GamePanel class is created.
The second line calls the newPaddles() method, which creates new paddle objects.
The third line calls the newBall() method, which creates a new ball object.
The fourth line calls the setFocusable() method on the current GamePanel object and sets its value to true. This allows the panel to receive keyboard input.
The fifth line calls the addKeyListener() method on the current GamePanel object and adds a new KeyAdapter object to it. This allows the panel to respond to key events.
The sixth line calls the setPreferredSize() method on the current GamePanel object and sets its size to the value of the SCREEN_SIZE constant.
The seventh line creates a new Thread object and assigns it to the gameThread variable. The "this" keyword is passed as a parameter, which means the current GamePanel object is being used as the thread's target.
The eigth line calls the start() method on the gameThread object, which starts the thread.

##Threading 
In the code, line 7 creates a new Thread object and assigns it to the gameThread variable. The "this" keyword is passed as a parameter, which means the current GamePanel object is being used as the thread's target. The thread is started on line 8 by calling the start() method. This means that the GamePanel class's run() method, which is implemented by the Runnable interface, will be executed on a separate thread.
When the GamePanel object is created, a separate thread is created and started by the constructor of the GamePanel class on line 7 and 8. This thread's target is the GamePanel object itself, which means that its run() method is executed on this separate thread.
This separate thread is responsible for running the game loop. The game loop is a loop that updates the game's state, redraws the screen, and checks for user input and other events. This loop is executed repeatedly on the separate thread, which allows the game to run at a steady frame rate and provide a smooth user experience.
So, the multiple threads in this code are the main thread and the thread created by the GamePanel constructor. The main thread is running the main method of the application and the thread created by the GamePanel constructor is running the game loop. Both threads are running simultaneously in a single process and share the resources of the application. The main thread is responsible for creating the GamePanel object and setting it up on the screen. The separate thread is responsible for updating the game's state and redrawing the screen.


##Paddles.java
The first line imports the java.awt package, which contains classes for creating and manipulating graphical elements such as colors, fonts, and layouts.
The second line imports the java.awt.event package, which contains classes for handling events in a GUI such as key presses and mouse clicks.
The third line declares the Paddles class, which extends the Rectangle class, which is a basic class for creating rectangles with specified properties.
The fourth line declares an int variable named id.
The fifth line declares an int variable named yVelocity.
The sixth line declares an int variable named speed and assigns the value 10 to it.
The seventh line defines the constructor for the Paddles class, which takes in parameters x, y, PADDLE_WIDTH, PADDLE_HEIGHT and id. This constructor calls the super class's constructor with the same parameters and also assigns the value of id to the id variable.
The eigth line defines the method draw which takes in parameter of Graphics g and sets the color of the paddle based on its id, it then fill the rectangle with the specified color.
The nineth line defines the method keyPressed which takes in parameter of KeyEvent e, it then checks the id of the paddle and based on the id it sets the y direction of the paddle.
The tenth line defines the method keyReleased which takes in parameter of KeyEvent e, it then checks the id of the paddle and based on the id it sets the y direction of the paddle to 0.
The eleventh line defines the method setYDirection which takes in parameter of int i, it then sets the value of yVelocity to the passed value.
The twelfth line defines the method move which updates the y position of the paddle based on the yVelocity.

## setYDirection(int i) {
In simple terms, setYDirection method is used to set the speed and direction of the paddle's movement in y-axis and move method is used to update the position of the paddle on the screen based on the speed and direction set by setYDirection method.

The first method, setYDirection(int i), is used to set the y-velocity of the paddle. The method takes in a single integer parameter, 'i', and assigns its value to the instance variable yVelocity. yVelocity is an integer variable that is used to store the movement speed of the paddle in the y-axis. By setting the value of yVelocity, we are controlling the speed and direction of the paddle's movement.

The second method, move(), is used to update the position of the paddle on the screen. The method does not take any parameters. It simply adds the value of yVelocity to the current y-position of the paddle, and assigns the result to the y-position. This means that if yVelocity is positive, the paddle will move downwards on the screen, and if yVelocity is negative, the paddle will move upwards. By calling this move() method repeatedly, the paddle will continue to move in the y-direction until yVelocity is changed.

The x and y variables in the code are the instance variables of the Rectangle class, which Paddles class extends. These instance variables store the position of the rectangle on x and y axis. These variables are being used to update the position of the Paddle.


