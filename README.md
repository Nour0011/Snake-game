from turtle import Screen, Turtle from snake import Snake from food import Food from scoreboard import Scoreboard import time

screen = Screen() screen.setup(width=600, height=600) screen.bgcolor("black") screen.title("My Snake Game") screen.tracer(0)

#crat snake object from that class snake = Snake() food = Food() scoreboard = Scoreboard()

screen.listen() screen.onkey(snake.up, "Up") screen.onkey(snake.down, "Down") screen.onkey(snake.left, "Left") screen.onkey(snake.right, "Right")

game_is_on = True while game_is_on: screen.update() time.sleep(0.1)

snake.move()

if snake.head.distance(food) < 15:
    food.refresh()
    snake.extend()
    scoreboard.increase_score()
detect collision with wall
if snake.head.xcor() > 280 or snake.head.xcor() < -280 or snake.head.ycor() > 280 or snake.head.ycor() < -280:
    game_is_on = False
    scoreboard.game_over()

    # detect collision with tail

for segment in snake.segments[1:]:
    if snake.head.distance(segment) < 10:
        game_is_on = False
        scoreboard.game_over()
screen.exitonclick()

from turtle import Turtle

STARTING_positions = [(0, 0), (-20, 0), (-40, 0)] #constants are named with all caps MOVE_DISTANCE = 20 UP = 90 DOWN = 270 LEFT = 180 RIGHT = 0 class Snake:

in python class names in pascale case the first litter should be in capital
def __init__(self):
    self.segments = []
    self.create_snake()
    self.head = self.segments[0]
def create_snake(self):

    for position in STARTING_positions:
     self.add_segment(position)

def add_segment(self, position):

    new_segment = Turtle("square")
    new_segment.color("white")
    new_segment.penup()
    new_segment.goto(position)
    self.segments.append(new_segment)

def extend(self):
    #add a new segment to the snake
    #position in the turtle class
    self.add_segment(self.segments[-1].position())


def move(self):
    for seg_num in range(len(self.segments) - 1, 0, -1):
        new_x = self.segments[seg_num - 1].xcor()
        new_y = self.segments[seg_num - 1].ycor()
        self.segments[seg_num].goto(new_x, new_y)

    self.head.forward(MOVE_DISTANCE)

def up(self):
    if self.head.heading() != DOWN:
        self.head.setheading(UP)

def down(self):
    if self.head.heading() != UP:
        self.head.setheading(DOWN)

def left(self):
    if self.head.heading() != RIGHT:
        self.head.setheading(LEFT)

def right(self):
    if self.head.heading() != LEFT:
        self.head.setheading(RIGHT)
from turtle import Turtle

STARTING_positions = [(0, 0), (-20, 0), (-40, 0)] #constants are named with all caps MOVE_DISTANCE = 20 UP = 90 DOWN = 270 LEFT = 180 RIGHT = 0 class Snake:

in python class names in pascale case the first litter should be in capital
def __init__(self):
    self.segments = []
    self.create_snake()
    self.head = self.segments[0]
def create_snake(self):

    for position in STARTING_positions:
     self.add_segment(position)

def add_segment(self, position):

    new_segment = Turtle("square")
    new_segment.color("white")
    new_segment.penup()
    new_segment.goto(position)
    self.segments.append(new_segment)

def extend(self):
    #add a new segment to the snake
    #position in the turtle class
    self.add_segment(self.segments[-1].position())


def move(self):
    for seg_num in range(len(self.segments) - 1, 0, -1):
        new_x = self.segments[seg_num - 1].xcor()
        new_y = self.segments[seg_num - 1].ycor()
        self.segments[seg_num].goto(new_x, new_y)

    self.head.forward(MOVE_DISTANCE)

def up(self):
    if self.head.heading() != DOWN:
        self.head.setheading(UP)

def down(self):
    if self.head.heading() != UP:
        self.head.setheading(DOWN)

def left(self):
    if self.head.heading() != RIGHT:
        self.head.setheading(LEFT)

def right(self):
    if self.head.heading() != LEFT:
        self.head.setheading(RIGHT)
from turtle import Turtle import random

#food class inhrent from the turtle class class Food(Turtle):

def __init__(self):
    super().__init__()
    self.shape("circle")
    self.penup()
    self.shapesize(stretch_len=0.5, stretch_wid=0.5)
    self.color("blue")
    self.speed("fastest")
    self.refresh()

def refresh(self):
    random_x = random.randint(-200, 200)
    random_y = random.randint(-200, 200)
    self.goto(random_x, random_y)
from turtle import Turtle ALIGNMENT = "center" FONT = ("courier", 24, "normal") class Scoreboard(Turtle): def init(self): super().init() self.score = 0 self.color("white") self.penup() self.goto(0, 270) self.hideturtle() self.update_scoreboard()

def update_scoreboard(self):
    self.write(f"Score: {self.score}", align=ALIGNMENT, font=FONT)

def game_over(self):
    self.goto(0,0)
    self.write(f"GAME OVER", align=ALIGNMENT, font=FONT)
def increase_score(self):
    self.score += 1
    self.clear()
    self.update_scoreboard()
