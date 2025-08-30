# Ex-4 Rail-Fence-Program
```
NAME: SANKAR S
DEPT: B.E/CSE
REG NO: 212224040291
```
# IMPLEMENTATION OF RAIL FENCE – ROW & COLUMN TRANSFORMATION TECHNIQUE

# AIM:
To write a C program to implement the rail fence transposition technique.

# DESCRIPTION:

In the rail fence cipher, the plain text is written downwards and diagonally on successive "rails" of an imaginary fence, then moving up when we reach the bottom rail. When we reach the top rail, the message is written downwards again until the whole plaintext is written out. The message is then read off in rows.

# ALGORITHM:

STEP-1: Read the Plain text.
STEP-2: Arrange the plain text in row columnar matrix format.
STEP-3: Now read the keyword depending on the number of columns of the plain text.
STEP-4: Arrange the characters of the keyword in sorted order and the corresponding columns of the plain text.
STEP-5: Read the characters row wise or column wise in the former order to get the cipher text.

# PROGRAM
```
def encrypt_rail_fence(message, rails):
    if rails <= 1:
        print("Number of rails must be greater than 1.")
        return
    # Create the rail matrix and initialize with a placeholder
    rail = [['\n'] * len(message) for _ in range(rails)]
    # Traverse the rail matrix in a zigzag pattern to place the characters
    row, direction = 0, 1
    for i in range(len(message)):
        rail[row][i] = message[i]
        # Change direction at the top or bottom rail
        if row == 0:
            direction = 1
        elif row == rails - 1:
            direction = -1
        row += direction
    # Read the encrypted message from the rail matrix row by row
    result = []
    for i in range(rails):
        for j in range(len(message)):
            if rail[i][j] != '\n':
                result.append(rail[i][j])
    print("Encrypted text:", "".join(result))
def main():
    message = input("Enter a Secret Message: ").replace(" ", "").upper()
    try:
        rails = int(input("Enter number of rails: "))
        encrypt_rail_fence(message, rails)
    except ValueError:
        print("Invalid input. Please enter a valid number for rails.")

if __name__ == "__main__":
    main()
```
# OUTPUT

<img width="1450" height="669" alt="image" src="https://github.com/user-attachments/assets/c58d4d20-8129-4968-a377-a2cd072bd773" />

# RESULT
The program is executed successfully
