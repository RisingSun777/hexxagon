hexxagon
========

Hexxagon (a.k.a. Beehive chess) game in Java.
By Rising Sun
Starting date: 01/26/2013 1:11 AM
----------
1 - Board modeling
    A 2 dimensional array of 55 cells aligning Pascal-triangle-likely.
    The board is an fixed image. And the cells' coordinates will depend on this image.
    
    Each cell is a struct:
        status: 4 statuses - Empty, Player 1, Player 2, Player 3. Used to determine which piece occupy a cell.
        neighborlist: A list of its neighbor cells.
        final x, y: x, y constant coordinates. Its value will be determined by an algorithm, rather than manually input.
        draw(): draw the piece to the screen depending on the status attribute, x and y coordinate.
    
    Current turn variable: This variable will determine whether you can click on the piece to move.
    Moving a piece - flow:
        Click on a piece
        Check whether the piece is of the current player.
        Click on a neighborhood cell.
        Check whether that cell is occupied or neighborhood.
        This cell's status is Empty. The latter's holds the current player's piece.
        Check if a piece has conquered (a) neighborhood piece(s).
    
2 - The neighborlist:
    There are 3 cases:
        a. The cell is at the point of the triangle board. ie: cell[0][0], [9][0], [9][9]. These cells will have 2 neighbors.
        b. The cell is at the edge of the triangle board but not listed in a. These cells will have 4 neighbors.
        c. The rest. These cells will have 6 neighbors.