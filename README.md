Download Link: https://assignmentchef.com/product/solved-cmsc203-lab2-data-manager-lab
<br>
<strong>Overview: </strong>In the Graphical User Interface (GUI) Lab we will construct a simple GUI step by step.

<strong>Data Manager:</strong> (Provided to the student) It is good programming practice to separate functionality into distinct classes.  To accomplish this, GUI functionality is kept separate from the management of the application.  The DataManager does not interact with the user.  Rather, the GUI collects any user input like mouse-clicks and calls methods of the DataManager, and the DataManager reports results to the GUI which may be displayed to the user.  Within the DataManager, there are usually one or more Data Structures, which are populated with one or more types of Data Elements.  This DataManager has only simple functionality which does not require data structures other than simple fields.

<strong>FXDriver: </strong>(Initial version provided to the student) The class called <strong><em>FXDriver</em></strong> is the starting point for the FX version of the GUI.  FX is the framework we will use, and is available beginning with Java 8.  There are many ways to organize the GUI, but one way is to hold the basic startup features in a single simple file, which calls an instance of the main panel.

In FX, the <strong><em>main</em></strong> method (as in any Java application) is the starting point.  In FX it calls only the method <strong><em>launch(args)</em></strong>, where <strong><em>args</em></strong> is the array of data passed in to the application, usually <strong><em>null</em></strong>.  This launch method executes various setup code, hidden from the programmer, including creating a so-called “stage”, and calls the method <strong><em>start(Stage stage)</em></strong>;  Everything that the programmer wants to execute must be placed in <strong><em>start</em></strong>.

<strong>FXMainPane</strong>: (Initial version provided to the student) In this approach to GUI building, an instance of the class<strong><em> FXMainPane</em></strong> does all the programmer’s work of creating the GUI.  The initial version is simply a stub with a constructor, so that FXDriver will compile and run.

Each task has a comment in the java files such as //student Task #n

with a statement about what is to be accomplished.

<strong>Task #1</strong>

<ul>

 <li>Create a java project in Eclipse. Load the files FXDriver.java, FXMainPane.java, and DataManager.java from Blackboard into this project.</li>

 <li>In the FXDriver class, create an instance of <strong>FXMainPane</strong> and set it to a new instance of <strong>FXMainPane</strong> called</li>

 <li>Using the parameter called <strong>stage</strong> (provided by Java FX when <strong>launch</strong> calls <strong>start</strong>), call the method <strong>setScene(new Scene(root, </strong><em>[width]</em><strong>,</strong><em>[height]</em><strong>)); </strong>The parameters width and height specify the dimensions of the scene window in integer pixels.</li>

</ul>




Compile and run.  Note that a window appears, but does not have any content.







<strong>Task #2</strong>

Note that <strong>FXMainPane</strong> extends <strong>VBox</strong>, so the class is a <strong>VBox</strong>.

<ul>

 <li>In the <strong>FXMainPane</strong> class, declare five buttons, a label, and a textfield. Declare two <strong>HBox</strong>es that will hold the these components and go inside the <strong>VBox</strong>.</li>

</ul>




<ul>

 <li>Instantiate the buttons with the arguments “Hello”, “Howdy”, “Chinese“, Clear”, and “Exit”.</li>

</ul>




<ul>

 <li>Instantiate the label with the argument “Feedback:”.</li>

</ul>




<ul>

 <li>Instantiate the textfield.</li>

</ul>




<ul>

 <li>Instantiate the <strong>HBox</strong></li>

</ul>




Compile and run the <strong>FXDriver</strong>.

Note that even though the buttons and other components are instantiated, they do not appear in the window.

<strong> </strong>

<strong>Task #3</strong>

To cause components to appear, they must be added to a containing component, which itself is added to its containing component, all the way up to the component that is added to <strong>Scene</strong>.

<ul>

 <li>Add the buttons to one of the <strong>HBox</strong>es using <strong>getChildren().addAll(button1, etc…)</strong></li>

</ul>




<ul>

 <li>Add the label and the textfield to the other <strong>HBox</strong></li>

</ul>




<ul>

 <li>Add the <strong>HBox</strong>es to the <strong>FXMainPane</strong> (which is a <strong>VBox</strong>) using <strong>getChildren().addAll(…)</strong>. Note that we have already added <strong>FXMainPane</strong> to the new <strong>Scene</strong> in <strong>FXDriver</strong>.</li>

</ul>




Compile and run the <strong>FXDriver</strong>.

Note two things: The buttons do not respond to mouse-clicks, and the components are not well-spread, but are all positioned in the upper left corner of the containing window.<strong></strong>

<strong>Task #4</strong>

<ul>

 <li>Declare an instance of <strong>DataManager</strong> at the <strong>FXMainPane</strong> class level so that its scope extends throughout the class. Instantiate it in the constructor.</li>

</ul>




<ul>

 <li>To set the buttons to respond to mouse-clicks,

  <ol>

   <li>create an inner class at the class level (for example, called ButtonHandler) that implements <strong>EventHandler&lt;ActionEvent&gt;</strong>. For each button, use <strong>setOnAction(new ButtonHandler())</strong>.</li>

   <li>This interface requires the method <strong>handle(ActionEvent event)</strong> to be implemented. The mouse event is provided to the <strong>handle</strong> method, and <strong>getTarget()</strong> returns the object that caused the event, allowing a selection to be made.</li>

   <li>Implement an if-else-if structure that gets the target button that was selected and executes the appropriate block of code.

    <ol>

     <li>If the “Hello”, “Howdy” or “Chinese” buttons were selected, call the <strong>DataManager</strong> instance’s methods <strong>getHello</strong>, <strong>getHowdy</strong>, or <strong>getChinese</strong> and call the text field’s method <strong>setText</strong> with the response from the <strong>DataManager</strong>.</li>

     <li>If the “Clear” button was selected, call the text field’s method <strong>setText(“”);</strong> to clear out the text field.</li>

    </ol></li>

  </ol></li>

</ul>

<ul>

 <li>If the “Exit” button was selected, call <strong>exit(); </strong>and<strong> System.exit(0); </strong></li>

</ul>




<ul>

 <li>Position the components so they are generally centered and spaced apart.

  <ol>

   <li>To set margins for each component, call the static method on the containing component, e.g., <strong>setMargin(button1, inset); </strong>where <strong>inset</strong> is an instance of the class <strong>Inset</strong>.</li>

   <li>To center each <strong>HBox</strong>, use <strong>setAlignment(Pos.CENTER);</strong> where <strong>Pos</strong> is an Enum that will need to be imported.</li>

  </ol></li>

</ul>




<ul>

 <li><strong><em>JUST FOR FUN (optional)</em></strong>: create a sixth button that says “Hello” in another language. Add a method to the DataManager class to return the string.</li>

</ul>




<ul>

 <li>Add the files to GitHub in a directory named CMSC203_Lab2</li>

</ul>




Compile and run FXDriver.  Select each of the buttons to ensure they are working correctly.

Submit the three java files to Blackboard.  If any of these instructions is confusing to you, download and study the code in GUI_Template.zip in Week 4.