import numpy as np
import random as r

# Initialize board with strings
z3c3 = np.full((3, 3), "0")
mat = [(x, y) for x in range(3) for y in range(3)]

def valid_position(x, y):
    return 0 <= x <= 2 and 0 <= y <= 2

def Take_input():
    while True:
        try:
            coords = input("Enter your x and y (0-2, comma separated): ").strip()
            x, y = map(int, coords.split(","))
            if valid_position(x, y) and (x, y) in mat:
                z3c3[x][y] = "H"
                mat.remove((x, y))
                break
            else:
                print("Invalid or already taken position. Try again.")
        except Exception as e:
            print("Invalid format. Enter as x,y (e.g., 1,2)")

def take_assighn():
    if len(mat) == 0:
        return
    (t, p) = r.choice(mat)
    z3c3[t][p] = "C"
    print(f"Computer chose: ({t},{p})")
    mat.remove((t, p))

def is_win():
    for i in range(3):
        if len(set(z3c3[i])) == 1 and z3c3[i][0] != "0":
            return True
        if len(set(z3c3[:, i])) == 1 and z3c3[0][i] != "0":
            return True

    if len(set([z3c3[i][i] for i in range(3)])) == 1 and z3c3[0][0] != "0":
        return True
    if len(set([z3c3[i][2 - i] for i in range(3)])) == 1 and z3c3[0][2] != "0":
        return True

    return False

def game_start():
    print("Welcome to Tic-Tac-Toe (You = H, Computer = C)")
    while len(mat) != 0:
        Take_input()
        print(z3c3)
        if is_win():
            print("🎉 Haji win!")
            return
        if len(mat) == 0:
            break
        take_assighn()
        print(z3c3)
        if is_win():
            print("🤖 Computer wins!")
            return
    print("It's a draw!")

game_start()
