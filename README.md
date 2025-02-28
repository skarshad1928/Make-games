# Make-games
SOS-7 me comp 8
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
