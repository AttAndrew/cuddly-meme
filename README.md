# cuddly-meme
#For a class i have to create this tic tac toe game. the main things i need to do is define isValid and switchTurn (in bold), i have #spent hours on this but every time i run it all it does is draw a circle in the middle spot, i have to follow curtain things (which i #italicized). if anyone can help i would really appreciate it.

# Fall 2018
# This is the skeleton code to be used for this project.
#
import turtle

# Global variables which are needed
# DO NOT CHANGE
# Students should read all the variables to know what they mean
#
# define turtle, set speed max, make triangle go away
drawer = turtle.Turtle()
drawer.speed(0)
drawer.hideturtle()
drawer.pensize(2)
# define screen listener
screenListener = turtle.Screen()
# size of board
boardSize = 300
# A convenient constant for empty string
EMPTY = '-'
# The tic tac toe board is a 2D list, it is initialized in EMPTY
board = [[EMPTY, EMPTY, EMPTY], [EMPTY, EMPTY, EMPTY], [EMPTY, EMPTY, EMPTY]]
# turn is "X" for x's and "O" for o's. First turn is for o's.
turn = "O"
# keeps track if someone has won
winner = False
# End of global variables

'''
function should draw the tictactoe board

'''
# Assignment 6: Add the statements that will draw the tic-tac-toe board
# use global variable boardSize
# turtle name is drawer (see above in the global variables)

def drawBoard():
    drawer.penup()
    drawer.goto(-300, 250)
    drawer.pendown()
    drawer.forward(600)
    drawer.penup()
    drawer.goto(-300, 80)
    drawer.pendown()
    drawer.forward(600)
    drawer.penup()
    drawer.goto(-300, -80)
    drawer.pendown()
    drawer.forward(600)
    drawer.penup()
    drawer.goto(-300,-250)
    drawer.pendown()
    drawer.forward(600)
    drawer.penup()
    drawer.goto(90, 250)
    drawer.pendown()
    drawer.right(90)
    drawer.forward(500)
    drawer.penup()
    drawer.goto(-90, 250)
    drawer.pendown()
    drawer.forward(500)
    drawer.penup()


'''
function checks to see if the given row and column is a valid 
         position to place a piece (O or X, depending on the turn)

inputs: row and column which makes the position to be checked

return True if it is a valid position (empty)
return False if it is not a valid position (an O or X is already there)
'''
# Assignment 6: Add the statements to validate position as empty
# hint: use the EMPTY global constant to compare
#
def isValid(row,col):
    if board [row][col] == '-':
        return True
    else:
        return False


'''
inputs: row and column in which to draw the 'X'
'''
# Assignment 6: Add the statements to draw the X in the specified position
# and with the pen color shown on the examples.
#
def drawX(row,col):
    drawer.penup()
    drawer.goto(row,col)
    drawer.pendown()
    drawer.right(45)
    drawer.forward(50)
    drawer.right(180)
    drawer.forward(100)
    drawer.right(180)
    drawer.forward(50)
    drawer.left(90)
    drawer.forward(50)
    drawer.right(180)
    drawer.forward(100)
    drawer.right(180)
    drawer.forward(50)
    drawer.right(45)
    drawer.penup()

'''
inputs: row and column in which to draw the 'O'
'''
# Assignment 6: Add the statements to draw the O in the specified position
# and with the pen color shown on the examples
#
def drawO(row,col):
    drawer.penup()
    drawer.goto(row - 50,col)
    drawer.pendown()
    drawer.circle(50)
    drawer.penup()


'''
function switches turn by modifying the global variable 'turn'
'''
# Assignment 6: complete the statements of this function, which does the
# following:
# if the current turn is for the 'O' it is changed to 'X' and viceversa
#
def switchTurn():
    global turn
    if turn == "O":
        turn == "X"


# FROM THIS POINT UNTIL THE END, YOU MAY IGNORE THE CODE FOR NOW
'''
function should check if board is full
In other words no empty spaces in it

return True if board if full
return False if board is not full
'''
# Empty for now, will be written on Assignment #7
def isFull():
    return False


'''
function should call all 3 other check functions bellow

input: piece to check, piece can be O or X

returns True if the piece checked has won
return False if the piece checked has not won
'''
# Empty for now, will be written on Assignment #7
def checkWin(piece):
    return False


'''
function should check the diagonals of the board for a win

input: piece to check

returns True if the piece checked has won
return False if the piece checked has not won
'''
# Empty for now, will be written on Assignment #7
def checkDiagonalWin(piece):
    return False


'''
function should check each row of board for a win

input: piece to check

returns True if the piece checked has won
return False if the piece checked has not won
'''
# Empty for now, will be written on Assignment #7
def checkHorizontalWin(piece):
    return False


'''
function should check each column of board for a win

input: piece to check

returns True if the piece checked has won
return False if the piece checked has not won
'''
# Empty for now, will be written on Assignment #7
def checkVeritcalWin(piece):
    return False


# DO NOT CHANGE THIS FUNCTION
# called every time mouse is clicked
def clickEvent(x, y):
    global winner
    if abs(x) <= boardSize/2 and abs(y) <= boardSize/2 and (not winner):
        row = int(2 - (y + boardSize / 2) // (boardSize / 3))
        col = int((x + boardSize/2) // (boardSize/3))
        if isValid(row,col):
            board[row][col] = turn
            if turn == "O":
                drawO(row, col)
            else:
                drawX(row, col)
            checkStatus()

# DO NOT CHANGE THIS FUNCTION
def checkStatus():
    if checkWin(turn):
        won()
    elif isFull():
        full()
    else:
        switchTurn()


# DO NOT CHANGE THIS FUNCTION
def full():
    global winner
    # set font size
    fontSize = 30
    # sets winner to true
    winner = True
    # draws text stating winner
    drawer.penup()
    drawer.goto(-(boardSize / 2), boardSize / 2 + fontSize)
    drawer.pendown()
    drawer.setheading(0)
    drawer.color("black")
    drawer.write("Tied Game", font=("Arial", fontSize, "normal"))


# called when someone has won, to draw a message of who's the winner
# DO NOT CHANGE THIS FUNCTION
def won():
    global winner
    # set font size
    fontSize = 30
    # sets winner to true
    winner = True
    # draws text stating winner
    drawer.penup()
    drawer.goto(-(boardSize/2), boardSize/2 + fontSize)
    drawer.pendown()
    drawer.setheading(0)
    drawer.color("black")
    drawer.write("Winner is %s" % (turn), font =("Arial", fontSize, "normal"))


# Statements of the "main program"
# Draws the board by calling the function drawBoard.
# Then it just waits for the
# user to click on a position on the board.
# Nothing else is needed in this main program

drawBoard()

# mouse listener: to capture when the user clicks the mouse
#                 each player will click with the mouse on
#                 the position where they want to play
screenListener.onclick(clickEvent)

turtle.done()


