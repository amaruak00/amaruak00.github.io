---
layout: post
title: Botclean - Large
tags: [Hackerrank, AI]
excerpt_separator: <!--more-->
---

로봇 `b`가 m*n의 공간에서 `LEFT, RIGHT, UP, DOWN`으로 이동 후 `d`로 대응되는 먼지들을 `CLEAN`하는 문제. 이동 횟수가 `cost`이며, [유클리디안 거리를 사용한 예시가](https://github.com/Murillo/Hackerrank-Artificial-Intelligence/blob/master/Bot-Building/botclean-large.py) 있어 참고하여 코딩했다. 
<!--more-->
MegaMaid is a robot whose function is to move through a matrix and clean all of its dirty cells. It's positioned in some cell of an  matrix of dirty (d) and clean (-) cells. It can perform five types of operations:

----
* `LEFT`: Move one cell to the left.
* `RIGHT`: Move one cell to the right.
* `UP`: Move one cell up.
* `DOWN`: Move one cell down.
* `CLEAN`: Clean the cell.

**Input Format**
----
The first line contains two space-separated integers describing the respective  (row) and  (column) coordinates of MegaMaid's initial location.
The second line contains two space-separated integers describing the respective height, , and width, , of the matrix.
Each line  of the  subsequent lines contains a string of  characters describing row  in the matrix; each character  describes the character at location  according to the following key:
* `b` denotes MegaMaid's location (in a clean cell).
* `d` denotes a dirty cell.
* `-` denotes a clean cell.

----

**Note**: If MegaMaid is initially located in a dirty cell, the cell will be marked with a d (not a b).

**Output Format**
----
Print the next operation MegaMaid will perform (i.e., LEFT, RIGHT, UP, DOWN, CLEAN). It's important to only print the next operation, because your program will be called iteratively after performing each operation.

**Sample Input**
----
    0 0
    5 5
    b---d
    -d--d
    --dd-
    --d--
    ----d

**Sample Output**
----
    RIGHT
    Explanation

MegaMaid's next move would be to move RIGHT, resulting in the following next state:

----
    -b--d
    -d--d
    --dd-
    --d--
    ----d

----

    import math

    def get_dirt_nearest(posx, posy, dirties):
        dirt_distances = []
        for i in range(len(dirties)):
            dirt_distances.append(math.sqrt((posx - dirties[i][0]) **2 + (posy - dirties[i][1]) **2))
            
        return [x for (y, x) in sorted(zip(dirt_distances, dirties))][0]

    def next_move(posx, posy, dimx, dimy, board):
        posx, posy = posy, posx
        
        dirties = []
        for x in range(dimx):
            for y in range(dimy):
                if board[y][x] == 'd':
                    dirties.append([x, y])
                    
        dirt_nearest = get_dirt_nearest(posx, posy, dirties)
        
        if dirt_nearest[0] < posx:
            print("LEFT")
        elif dirt_nearest[0] > posx:
            print("RIGHT")
        elif dirt_nearest[1] < posy:
            print("UP")
        elif dirt_nearest[1] > posy:
            print("DOWN")
        else:
            print("CLEAN")
        

    if __name__ == "__main__":
        pos = [int(i) for i in input().strip().split()]
        dim = [int(i) for i in input().strip().split()]
        board = [[j for j in input().strip()] for i in range(dim[0])]
        next_move(pos[0], pos[1], dim[0], dim[1], board)

        # _input = ['0 0',
        # '5 5',
        # 'b---d',
        # '-d--d',
        # '--dd-',
        # '--d--',
        # '----d']
        # pos = [int(i) for i in _input[0].strip().split()]
        # dim = [int(i) for i in _input[1].strip().split()]
        # board = [[j for j in _input[i].strip()] for i in range(2, 2+dim[0])]

