import numpy as np
import random as r
list1=[0,0,0,0,0,0,0,0,0]
zero3c3=np.array(list1)
z3c3 = zero3c3.reshape(3,3)
mat=[(x,y)for x in range(0,3) for y in range(0,3)]
def valid_position(x,y):
    if 0<=x<=2 and 0<=y<=2:
        return True
    return False
def Take_input():
    x, y = map(int, input("Enter your x and y: ").split(","))
    if valid_position(x,y)and (x,y) in mat:
        z3c3[x][y] = 7
        mat.remove((x,y))
    else:
        take_input()
def take_assighn():
    if len(mat)==0:
        return
    (t,p)=r.choice(mat)
    z3c3[t][p]=8
    print(f"({t},{p}) position assighned 8")
    mat.remove((t,p))
def is_win():
    # Check rows
    for i in range(3):
        if len(set(z3c3[i])) == 1 and z3c3[i, 0] != 0:
            return True

    # Check columns
    for i in range(3):
        if len(set(z3c3[:, i])) == 1 and z3c3[0, i] != 0:
            return True

    # Check main diagonal
    if len(set(z3c3[i, i] for i in range(3))) == 1 and z3c3[0, 0] != 0:
        return True

    # Check secondary diagonal
    if len(set(z3c3[i, 2 - i] for i in range(3))) == 1 and z3c3[0, 2] != 0:
        return True

    return False

    
def game_start():
    while (len(mat)!=0):
        Take_input()
        print(z3c3)
        if is_win():
            print("you win")
            return
        take_assighn()
        print(z3c3)
        if is_win():
            print("comp win")
            return
game_start()
