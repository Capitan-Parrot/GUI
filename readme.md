# Pygame GUI

### What is it ?
 This librairy aims to provide simple widget to improve pygame applications like buttons, text or math text widgets.

### Dependancies
* **pygame :**   This library is fully based on pygame, so you must have it installed.

*(optionnal)*
* **latex :** you must avec latex install if you want to use the `LaText` widget 
            (`latex` and `dvipng` accessible in path)

### Installation
 You can clone this repository in your project or just run
        
    pip install git+https://github.com/ddorn/GUI.git@master#egg=GUI    

### Use

##### Bases
Every widget has a `pos`, a `size` and an `anchor`, both can be function or callbacks with no parameters.
The `pos` and the `size` defines a `pygame.Rect` where the widget is. The `pos`is per default the center of the widget, 
but you can change this behavior by giving an other `anchor`, like `TOPLEFT`. 

##### Tree steps to use a button


Every widget is totally independent and will do nothing unless you tell him to do something.
There is no theading thing that continuously check for events both for performance and to give you more cotrol on the widgets.

For instance, widget won't auto-render on the screen and wont listen events, like clics on buttons.  
Thus, to have a fully operational button there is three steps :

Just define it, nothing complex once you've read the bases.

    # define the action the button will perform when clicked
    def callback():
        print('PRESSED !")
        
    button = Button(callback, (100, 100), (100, 40), "Click Me !")

Then, you must continuously check for events, and call `press()` when you want. 
(typically when the user clicks the buton)

    for e in pygame.events.get():
        if e.type == pygame.MOUSEBUTTONDOWN and e.button == 1:  # left click
            if pygame.mouse.get_pos() in button:
                button.press()  # you tell the button to call the callback if clicked

And finally you must render the button on the screen.
                    
     button.render(display)  # you draw the button on the display

It's basically the same thing for any widget, except for "passive" widgets like texts, because 
we do not bother if the user clicks it.

##### Limitations

 As always with pygame, do not try to make too big apps with a lot of changing texts or with too big protions of the screen
 that are too often redrawn or it can lag a bit. 

### Help and todo list

You're welcome ! 

###### How can you help ?
 Do not hesitate to [contact me](mailto:diego.dorn@free.fr) to discuss aboute code, optimisation or functionnalities. 
 You can of course make any push request you want !  
 Feel free to report any issue you see as I do not have strong tests (I mean, no tests !)
 

###### Todos : 
 * A `Text` class to make texts that goes on more lines and with wrapping.
 * A `TextBox`, of course
 * A `RichText` to make text with differents inner colors/size/font/styles
 * Something like lists
 * `Switch` class : Nice looking ON/OFF button
 * Some geometry function to draw curves, grids and manipulate line, polygons
 
 This is absolutly not an ordered list, they will come as I have nice looking and useable classes !
 

### Cool projects with this library

Do not hesitate to tell me if you have something working !  
Here is a list of projets that uses my library, take inspiration !

 * [**Crabes**](https://github.com/ddorn/crabes) : a simulation too for a [TFJM²](https://www.tfjm.org/) problem
 * Your project !
 
Examples at the and of each file can also give you a lot of samples of how to use this library :)