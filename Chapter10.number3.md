 Write a program to play "Three Button Monte." Your program should draw three buttons labeled "Door 1" "Door 2" and "Door 3" in a window and ' ' randomly select one of the buttons (without telling the user which one is selected). The program then prompts the user to click on one of the buttons. A click on the special button is a win, and a click on one of the other two is a loss. You should tell the user whether they won or lost, and in the case of a loss, which was the correct button. Your program should be entirely graphical; that is, all prompts and messages should be displayed in the graphics window. 
================================================================
1. Make graphwindow object, a text object and three button object
2. create the graphwindow
3. select a dooornumber
4. get a choice form user
5. if user won
6. display the result
7. close the window after another mouseclick


```python
#monte_menu
class Menu:
    def __init__(self, win,prompt, butn1, butn2, butn3):
        self.win = win
        self.prompt = promt
        self.butn1 = butn1
        self.butn2 = butn2
        self.butn3 = butn3

    def setprompt(self, tet):
        self.prompt.setText(text)

    def butn1_clicked(self, pt):
        return self.butn1.clicked(pt)
    
    def butn2_clicked(self, pt):
        return self.butn2.clicked(pt)

    def butn3_clicked(self, pt):
        return self.butn3.clicked(pt)

    def button_clicked(self,pt):
        return (self.butn1.clicked(pt) or self.butn2.clicked(pt) or self.butn3.clicked(pt))

    def dactivate_butns(self):
        self.butn1.deactivate()
        self.butn2.deactivate()
        self.butn3.deactivate()

    def getMouse(self):
        return self.win.getMouse()

    def colse(self):
        return self.win.close()
```

-------------------------------------------
```python
from graphics import *
from random import randrage
from button import Button
from monte_menu import Menu

def main():
    menu  = drawWin()
    door = chooseDoor()
    choice = getChoice(menu)
    correct = isCorrect(door, choice)
    updateWin(menu, correct)

    menu.getMouse()
    menu.close()

def drawWin():
    win = GraphWin("Three Door Monte", 400, 100)
    win.setCoords(0, 0, 12, 2)
    instr = Text(Point(6,1.5), "Which one? What do you want?")
    instr.setSise(11)
    instr.draw(win)
    butn1 = Button(win, Point(2, 0.5), 2, 1,"Door1")
    butn1.activate()
    butn2 = Button(win, Point(6, 0.5), 2, 1,"Door2")
    butn2.activate()
    butn3 = Button(win, Point(10, 0.5), 2, 1,"Door3")
    butn3.activate()
    menu=Menu(win,instr,butn1,butn2,butn3)
    return menu

def chooseDoor():
    winning_door = randrage(1,4)
    return winning_door

def getChoice(menu):
    pt=menu.getMouse()
    while not menu.button_clicked(pt):
        pt= menu.getMouse()
    if menu.butn1_clicked(pt):
        return 1
    elif menu.butn2_cliced(pt):
        return 2
    else :
        return 3


def isCorrect(door, choice):
    if choice  == door:
        return True
    else:
        return False

def updateWin(menu, correct):
    menu.deactivate_butns()
    if correct:
        menu.setPrompt("you win")
    else:
        menu.setPrompt("bye ~~")


main()
```
