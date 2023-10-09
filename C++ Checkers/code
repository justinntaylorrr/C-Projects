#include <iostream>

// Includes the files from the SFML library used to open my window and graphical user interface.
#include <SFML/Graphics.hpp>
#include <SFML/Window.hpp>


using namespace std; // Used to bring all the identifiers from the standard C++ library.

class gameBoard
{
	// REFERENCE for following code: https://www.sfml-dev.org/tutorials/2.5/graphics-draw.php // https://www.sfml-dev.org/tutorials/2.5/graphics-shape.php // https://www.sfml-dev.org/documentation/2.5.1/classsf_1_1RenderWindow.php
	// https://www.sfml-dev.org/tutorials/2.5/graphics-transform.php // https://www.sfml-dev.org/documentation/2.5.1/classsf_1_1Color.php

public: // Allows all the members inside this class to be accessed in and outside of it.

	void Draw(sf::RenderWindow & window) // The function to draw the game board onto an SFML window.
	{
		sf::RectangleShape tile; // Creates a rectangle shape for each tile on the board.
		sf::Color brown(101, 49, 0); // Defines a custom brown color for the tiles.
		sf::Color cream(255, 230, 207); // Defines a cream color for the tiles.

		tile.setSize(sf::Vector2f(100, 100)); // Sets the size of each tile to 100x100 pixels.
		for (int row = 0; row < 8; row++) // Loops through each row of the game board.
		{
			for (int col = 0; col < 8; col++) // Loops through each column of the game board.
			{
				tile.setPosition(sf::Vector2f(100.f * col, 100.f * row)); // Sets the position of the tile based on its row and column.
				if ((row + col) % 2 == 0) // Checks if the sum of the row plus the column is even.
				{
					tile.setFillColor(sf::Color(brown)); // If it is even, it sets the tile color to brown.
				}
				else
				{
					tile.setFillColor(sf::Color(cream)); // If it is odd, it sets the tile color to cream.
				}
				window.draw(tile); // Draws the tiles onto the SFML window.
			}
		}
	}

};

class Pieces
{

	// REFERENCE for following code: https://www.sfml-dev.org/tutorials/2.5/graphics-draw.php // https://www.sfml-dev.org/tutorials/2.5/graphics-shape.php // https://www.sfml-dev.org/documentation/2.5.1/classsf_1_1RenderWindow.php
	// https://www.sfml-dev.org/tutorials/2.5/graphics-transform.php // https://www.sfml-dev.org/documentation/2.5.1/classsf_1_1Color.php

	public: // Allows all the members inside this class to be accessed in and outside of it.
	int a = 0; // Variable named 'a' to store the row position of the pieces on the game board.
	int b = 0; // Variable named 'b' to store the column position of the pieces on the game board.
	float r = 40.f; // Variable named 'r' to store the radius of each piece.
	bool KingPiece = false; // Variable named 'KingPiece' to store whether the piece is a king piece or not.
	bool PieceAlive = false; // Variable named 'PieceAlive' to store whether the piece is alive or dead.


	sf::Color color; // Declares a variable named color of type 'sf::Color' which is from the SFML library to represent colors for graphic rendering.


	void Draw(sf::RenderWindow& window) // The function to draw the game board onto an SFML window.
	{
		if (PieceAlive) // Checks if the piece is alive.
		{
			sf::CircleShape circle(r); // Creates a circle shape with radius 'r' and variable name 'circle' through the function 'sf::CircleShape' which is from the SFML library to generate a shape graphic.
			circle.setFillColor(color); // Sets the fill color of the circle to 'color'.

			if (KingPiece) // Checks if it is a king piece.
			{
				circle.setOutlineThickness(10.f); // If the piece is a king piece, it sets an outline of the circle with thickness '10', using the setOutLineThickness function from SFML library.
				circle.setOutlineColor(sf::Color::Black); // Then sets the outline color of the circle to black.
			}

			circle.setPosition(sf::Vector2f(a * 100 + (100 - r * 2) / 2, b * 100 + (100 - 2 * r) / 2)); 
			// This formula determines the width and height of the area on the game board in '(100 - r * 2)'.
			// It then divides that result by 2, which gives the offset needed to place a piece in the centre of the tile. It then gets added to the next calculation.
			// 'a * 100' is to represent the row position of the piece on the board.
			// So overall it gives the x-coordinate of the piece.
			// The same is done on the right hand side to give the y-coordinate of the piece.

			window.draw(circle); // Draws the pieces onto the window.
		}

	}

};

void loadPieces(sf::RenderWindow& window, Pieces* CreamPieces, Pieces* BlackPieces)
{

	// REFERENCE for following code: https://www.w3schools.com/cpp/cpp_for_loop.asp

	int x = 0; // Initializes variable named 'x' to 0.
	
	for (int row = 5; row < 8; row++) // Loops through row 5, then 'row++' increments to loop through row 6 and then row 7.
	{
		for (int col = row % 2; col < 8; col += 2) // Loops through columns based on row being even or odd. Increments by 2 each loop.
		{
			
			BlackPieces[x].PieceAlive = true; // Sets the black piece to 'alive'
			BlackPieces[x].a = col; // Sets the value of 'a' of the x-th object in the 'BlackPieces' array to the current value of col
			BlackPieces[x].b = row; // Sets the value of 'a' of the x-th object in the 'BlackPieces' array to the current value of row
			x++; // Increments x by 1

		}
				 
	}
	x = 0; // Initializes variable named 'x' to 0.
	for (int row = 0; row < 3; row++) // Loops through row 0, then 'row++' increments to loop through row 1 and then row 2.
	{

		for (int col = row % 2; col < 8; col += 2) // Loops through columns based on row being even or odd. Increments by 2 each loop.
		{

			CreamPieces[x].PieceAlive = true; // Sets the crema piece to 'alive'
			CreamPieces[x].a = col; // Sets the value of 'a' of the x-th object in the 'BlackPieces' array to the current value of col
			CreamPieces[x].b = row; // Sets the value of 'a' of the x-th object in the 'BlackPieces' array to the current value of row
			x++; // Increments x by 1

		}

	}

}

Pieces* IsOccupied(int a, int b, Pieces* BlackPieces, Pieces* CreamPieces)
{

	// REFERENCE for following code: https://www.w3schools.com/cpp/cpp_for_loop.asp // https://www.geeksforgeeks.org/null-pointer-in-c/


	for (int x = 0; x < 12; x++) // Loops through all 12 black pieces
	{
		if (BlackPieces[x].a == a && BlackPieces[x].b == b) // Checks is 'a' and 'b' of the selection is equal to 'a' and 'b' of a piece in a the 'BlackPieces' array, if so a piece is present in that position.
		{
			if (BlackPieces[x].PieceAlive) // Checks if the piece is alive.
			{
				return &BlackPieces[x]; // Returns a pointer to the x-th object in the 'BlackPieces' array.
			}
		}
			
		if (CreamPieces[x].a == a && CreamPieces[x].b == b) // Checks is 'a' and 'b' of the selection is equal to 'a' and 'b' of a piece in a the 'CreamPieces' array, if so a piece is present in that position.
		{
			if (CreamPieces[x].PieceAlive) // Checks if the piece is alive.
			{
				return &CreamPieces[x]; // Returns a pointer to the x-th object in the 'CreamPieces' array.
			}

		}

	}
	return nullptr; // If no piece is found in that position, returns a null pointer.
}

void KillPiece(int a, int b, Pieces* CreamPieces, Pieces* BlackPieces, int* player)
{
	
	// REFERENCE for following code: https://www.geeksforgeeks.org/arrow-operator-in-c-c-with-examples/ // https://cplusplus.com/doc/tutorial/pointers/

	IsOccupied(a, b, CreamPieces, BlackPieces)->PieceAlive = false; // Call the function IsOccupied, to check if there is a piece present in that position, and then set this piece to 'dead' to kill the piece.
	
	if (*player == 1) // Check if it was player 1's move
	{
		*player = 2; // If it was, change it to player 2's move.
	}
	
	else 
	{
		*player = 1; // It was player 2's move originally, sets it to player 1's move.
	}
	
	return;
}

int MovePiece(int a, int b, Pieces* BlackPieces, Pieces* CreamPieces, int* player, Pieces*ChosenPiece)
{

	// REFERENCE for following code: https://www.geeksforgeeks.org/arrow-operator-in-c-c-with-examples/ // https://cplusplus.com/doc/tutorial/pointers/ // https://www.sfml-dev.org/documentation/2.5.1/classsf_1_1Color.php
	
		// Checks if the color of the chosen piece is cream, or if it's a black king piece, as they are the only pieces who can perform diagonally down left or right moves.
		if (ChosenPiece->color == sf::Color(228, 218, 199) || ChosenPiece->color == sf::Color::Black && ChosenPiece->KingPiece) 
		{
			// Checks if the player wants to move to the position diagonally down to the left.
			if (a == ChosenPiece->a - 1 && b == ChosenPiece->b + 1)
			{
				if (!IsOccupied(a, b, BlackPieces, CreamPieces)) // Checks if the place the piece is moving to is not occupied by another piece.
				{
					if (*player == 1) // Check if it was player 1's move
					{
						*player = 2; // If it was, change it to player 2's move.
					}

					else
					{
						*player = 1; // It was player 2's move originally, sets it to player 1's move.
					}

					// Updates the column and row position of the piece to it's new position.
					ChosenPiece->a = a; 
					ChosenPiece->b = b;

					return 1; // Returns 1 to show move was valid and complete.

				}

			}

			// Checks if the player wants to move to the position diagonally down to the right.
			if (a == ChosenPiece->a + 1 && b == ChosenPiece->b + 1)
			{
				if (!IsOccupied(a, b, BlackPieces, CreamPieces)) // Checks if the place the piece is moving to is not occupied by another piece.
				{
					if (*player == 1) // Check if it was player 1's move
					{
						*player = 2; // If it was, change it to player 2's move.
					}

					else
					{
						*player = 1; // It was player 2's move originally, sets it to player 1's move.
					}

					// Updates the column and row position of the piece to it's new position.
					ChosenPiece->a = a;
					ChosenPiece->b = b;

					return 1; // Returns 1 to show move was valid and complete.

				}

			}

			// Checks if the player wants to take an oppsition's piece which is in a position diagonally down to the right.

			if (a == ChosenPiece->a + 2 && b == ChosenPiece->b + 2) // Checks if the chosen move is 2 tiles across and 2 down, to simulate a jump over.
			{
				// Firstly checks if the position diagonally down to the right is occupied
				// It then checks if the place it is moving to is not occupied
				// Then it finally checks if the piece that is being taken is not the same color as the piece moving.
				if (IsOccupied(a + 1, b + 1, CreamPieces, BlackPieces) != NULL && (!IsOccupied(a, b, CreamPieces, BlackPieces)) && IsOccupied(a + 1, b + 1, CreamPieces, BlackPieces)->color != ChosenPiece->color)
				{

					if (*player == 1) // Check if it was player 1's move.
					{
						*player = 2; // If it was, change it to player 2's move.
					}

					else
					{
						*player = 1; // It was player 2's move originally, sets it to player 1's move.
					}

					KillPiece(a + 1, b + 1, CreamPieces, BlackPieces, player); // Calls the 'KillPiece' function using the piece that is being jumped over, so it is removed from the board.
					
					// Updates the position of piece that has performed the kill.
					ChosenPiece->a = a; 
					ChosenPiece->b = b;

					return 1; // Returns 1 to show move was valid and complete.

				}

			}

			// Checks if the player wants to take an oppsition's piece which is in a position diagonally down to the left.

			if (a == ChosenPiece->a - 2 && b == ChosenPiece->b + 2) // Checks if the chosen move is 2 tiles across and 2 down, to simulate a jump over.
			{
				// Firstly checks if the position diagonally down to the left is occupied
				// It then checks if the place it is moving to is not occupied
				// Then it finally checks if the piece that is being taken is not the same color as the piece moving.
				if (IsOccupied(a - 1, b + 1, CreamPieces, BlackPieces) != NULL && (!IsOccupied(a, b, CreamPieces, BlackPieces)) && IsOccupied(a - 1, b + 1, CreamPieces, BlackPieces)->color != ChosenPiece->color)
				{

					if (*player == 1) // Check if it was player 1's move.
					{
						*player = 2; // If it was, change it to player 2's move.
					}

					else
					{
						*player = 1; // It was player 2's move originally, sets it to player 1's move.
					}

					KillPiece(a - 1, b + 1, CreamPieces, BlackPieces, player); // Calls the 'KillPiece' function using the piece that is being jumped over, so it is removed from the board.
					
					// Updates the position of piece that has performed the kill.
					ChosenPiece->a = a;
					ChosenPiece->b = b;

					return 1; // Returns 1 to show move was valid and complete.

				}

			}

		}

		// Checks if the color of the chosen piece is black, or if it's a cream king piece, as they are the only pieces who can perform diagonally up left or right moves.

		if (ChosenPiece->color == sf::Color::Black || ChosenPiece->color == sf::Color(228, 218, 199) && ChosenPiece->KingPiece)
		{

			// Checks if the player wants to move to the position diagonally up to the left.
			if (a == ChosenPiece->a - 1 && b == ChosenPiece->b - 1)
			{
				if (!IsOccupied(a, b, BlackPieces, CreamPieces)) // Checks if the place the piece is moving to is not occupied by another piece.
				{
				{
					if (*player == 1) // Check if it was player 1's move.
					{
						*player = 2; // If it was, change it to player 2's move.
					}

					else
					{
						*player = 1; // It was player 2's move originally, sets it to player 1's move.
					}
					}
				 
					// Updates the column and row position of the piece to it's new position.
					ChosenPiece->a = a;
					ChosenPiece->b = b;

					return 1; // Returns 1 to show move was valid and complete.

				}

			}

			// Checks if the player wants to take an oppsition's piece which is in a position diagonally up to the left.
			if (a == ChosenPiece->a - 2 && b == ChosenPiece->b - 2)
			{

				// Firstly checks if the position diagonally up to the left is occupied
				// It then checks if the place it is moving to is not occupied
				// Then it finally checks if the piece that is being taken is not the same color as the piece moving.
				if (IsOccupied(a - 1, b - 1, CreamPieces, BlackPieces) != NULL && (!IsOccupied(a, b, CreamPieces, BlackPieces)) && IsOccupied(a - 1, b - 1, CreamPieces, BlackPieces)->color != ChosenPiece->color)
				{

					if (*player == 1) // Check if it was player 1's move.
					{
						*player = 2; // If it was, change it to player 2's move.
					}

					else
					{
						*player = 1; // It was player 2's move originally, sets it to player 1's move.
					}

					KillPiece(a - 1, b - 1, CreamPieces, BlackPieces, player); // Calls the 'KillPiece' function using the piece that is being jumped over, so it is removed from the board.
					
					// Updates the position of piece that has performed the kill.
					ChosenPiece->a = a;
					ChosenPiece->b = b;

					return 1; // Returns 1 to show move was valid and complete.

				}

			}


			// Checks if the player wants to move to the position diagonally up to the right.
			if (a == ChosenPiece->a + 1 && b == ChosenPiece->b - 1)
			{
				if (!IsOccupied(a, b, BlackPieces, CreamPieces)) // Checks if the place the piece is moving to is not occupied by another piece.
				{
					if (*player == 1) // Check if it was player 1's move.
					{
						*player = 2; // If it was, change it to player 2's move.
					}

					else
					{
						*player = 1;  // It was player 2's move originally, sets it to player 1's move.
					}

					// Updates the column and row position of the piece to it's new position.
					ChosenPiece->a = a;
					ChosenPiece->b = b;

					return 1; // Returns 1 to show move was valid and complete.

				}

			}

			// // Checks if the player wants to take an oppsition's piece which is in a position diagonally up to the right.
			if (a == ChosenPiece->a + 2 && b == ChosenPiece->b - 2)
			{

				// Firstly checks if the position diagonally up to the right is occupied
				// It then checks if the place it is moving to is not occupied
				// Then it finally checks if the piece that is being taken is not the same color as the piece moving.
				if (IsOccupied(a + 1, b - 1, CreamPieces, BlackPieces) != NULL && (!IsOccupied(a, b, CreamPieces, BlackPieces)) && IsOccupied(a + 1, b - 1, CreamPieces, BlackPieces)->color != ChosenPiece->color)
				{

					if (*player == 1) // Check if it was player 1's move.
					{
						*player = 2; // If it was, change it to player 2's move.
					}

					else
					{
						*player = 1; // It was player 2's move originally, sets it to player 1's move.
					}

					// Calls the 'KillPiece' function using the piece that is being jumped over, so it is removed from the board.
					KillPiece(a + 1, b - 1, CreamPieces, BlackPieces, player);

					// Updates the position of piece that has performed the kill.
					ChosenPiece->a = a;
					ChosenPiece->b = b;

					// Returns 1 to show move was valid and complete.
					return 1;

				}

			}

		}

		return 0;

	
}

int main()
{

	// REFERENCES for following code: https://www.sfml-dev.org/tutorials/2.5/window-window.php // https://www.sfml-dev.org/documentation/2.5.1/classsf_1_1Color.php 
	// https://www.sfml-dev.org/tutorials/2.5/window-inputs.php // https://cplusplus.com/doc/tutorial/pointers/ // https://www.sfml-dev.org/tutorials/2.5/window-events.php
	// https://www.sfml-dev.org/documentation/2.5.1/classsf_1_1Mouse.php // https://www.w3schools.com/cpp/cpp_for_loop.asp // 

	// Creates a window for the program to load the GUI through SFML. It sets the 800x800 pixel resolution and names the window.
	sf::RenderWindow window(sf::VideoMode(800, 800), "Checkers in C++; Justin Taylor (N1147482)");
	sf::Event event; // Creates an SFML event object named 'event' to handle events.

	// Creates two arrays for 12 Cream Pieces and 12 Black Pieces.
	Pieces CreamPieces[12]; 
	Pieces BlackPieces[12];
	
	gameBoard board; // Creates variable 'board' containing the attribrutes of the class 'gameBoard'.
	int map[8][8]; // Creates an 8x8 2D array for the board with variable name 'map'.
	int player = 1; // Sets the first turn to Player 1.

	bool selected = false; // Initialises and creates a boolean of variable name 'selected' to false, to represent if a piece has been selected.
	Pieces* ChosenPiece = NULL; // Initalises 'Chosen Piece' variable as a pointer of Pieces and sets to NULL.
	
	for (int x = 0; x < 12; x++) // Loops through all 12 pieces.
	{
		
		sf::Color cream(228, 218, 199); // Defines a custom cream color for the pieces.

		BlackPieces[x].color = sf::Color::Black; // Sets every piece in the array 'BlackPieces' to 'Black'.
		CreamPieces[x].color = sf::Color(cream); // Sets every piece in the array 'CreamPieces' to 'Cream'.

	}

	loadPieces(window, CreamPieces, BlackPieces); // Loads game pieces onto the window using the 'loadPieces' function.

	 // Runs the program as long as the window is open.
	while (window.isOpen())
	{

		// Checks through each event that has been triggered since the last loops iteration.
		while (window.pollEvent(event))
		{

			// Checks if the event requested is a close event.
			if (event.type == sf::Event::Closed)
			{

				window.close(); // If it is, the window is closed.

			}

			if (event.type == sf::Event::MouseButtonPressed) // Checks if the event requested is a Mouse Button Press event.
			{

				if (event.mouseButton.button == sf::Mouse::Left) // Checks if the mouse button pressed is the left mouse button.
				{

					selected = !selected; // If it is, it toggles selected, to become true.

				}

			}

		}
	

		window.clear(); // Clears the window.
		
		board.Draw(window); 
		for (int x = 0; x < 12; x++)
		{

			// Draws all 24 pieces onto the board.
			BlackPieces[x].Draw(window);
			CreamPieces[x].Draw(window);

		}
	
		// Checks if any game pieces have reached the opposite end of the board to become King Pieces.
		for (int x = 0; x < 12; x++) {
			if (BlackPieces[x].b == 0) {
				BlackPieces[x].KingPiece = true;
			}
			if (CreamPieces[x].b == 7) {
				CreamPieces[x].KingPiece = true;
			}
		}

		if (selected) // If a piece is selected by a player...
		{

			// Takes the x and y coordinates of the mouse click and converts them into to board coordinates to locate the pieces position on the board.
			int a = sf::Mouse::getPosition(window).x / 100;
			int b = sf::Mouse::getPosition(window).y / 100;

			// Checks if the position chosen by the mouse is occupied by a piece, 
			// If there is a piece present, it then it checks if the color of the piece is either cream and if the player is player 1,
			// Or if the piece is black and the player is player 2.
			if (IsOccupied(a, b, BlackPieces, CreamPieces) && (IsOccupied(a, b, BlackPieces, CreamPieces)->color == sf::Color(228, 218, 199) && player == 1) || (IsOccupied(a, b, BlackPieces, CreamPieces)->color == sf::Color::Black && player == 2))
			{

				// This means that the player has clicked on the same piece again, indicating that they want to deselect it. ChosenPiece is then set to NULL, deselecting the piece.
				if (IsOccupied(a, b, CreamPieces, BlackPieces) == ChosenPiece)
				{
					ChosenPiece = NULL;
				}

				else // This means that the player has clicked on a different piece, so a new piece is selected.
				{
					
					ChosenPiece = IsOccupied(a, b, CreamPieces, BlackPieces);

				}

				
				selected = false; // Set selected to false, move is completed, no piece is selected.

			}

			// If the chosen piece is not NULL and a valid move can be made at the point where the player has chosen to move the piece to, set selected to false and chosen piece to NULL.
			// This indicates that the move is completed and now no piece is selected.
			else if (MovePiece(a, b, BlackPieces, CreamPieces, &player, ChosenPiece) && ChosenPiece != NULL)
			{

				selected = false; 
				ChosenPiece = NULL;

			}

			selected = false; // Set selected to false, move is completed, no piece is selected.
		}
		
		window.display(); // This is from the SFML library, and it updates the display to make any changes made to the GUI.

	}
	
	return 0;
	
}
