# The playing grid

play_field_0 = [" ", " ", " "]
play_field_1 = [" ", " ", " "]
play_field_2 = [" ", " ", " "]
player_grid = [play_field_0, play_field_1, play_field_2]

# Since there are cells between the playing grid that not used,
# playing grid is separate from the whole grid for easier computing further

grid_line_0 = ["┌", "─", "─", "1", "─", "2", "─", "3", "─", "─", "┐"]
grid_line_1 = ["1", " ", "|", player_grid[0][0], "|", player_grid[0][1], "|", player_grid[0][2], "|", " ", "1"]
grid_line_2 = ["2", " ", "|", player_grid[1][0], "|", player_grid[1][1], "|", player_grid[1][2], "|", " ", "2"]
grid_line_3 = ["3", " ", "|", player_grid[2][0], "|", player_grid[2][1], "|", player_grid[2][2], "|", " ", "3"]
grid_line_4 = ["└", "─", "─", "1", "─", "2", "─", "3", "─", "─", "┘"]

# ▼▼▼▼▼for test▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼▼
# grid_line_0 = ("─", "─", "─", "─", "─", "─", "─")
# grid_line_1 = ("|", "1", "|", "2", "|", "3", "|")
# grid_line_2 = ("|", "4", "|", "5", "|", "6", "|")
# grid_line_3 = ("|", "7", "|", "8", "|", "9", "|")
# grid_line_4 = ("─", "─", "─", "─", "─", "─", "─")
# ▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲▲

# full grid
ttt_grid = [grid_line_0, grid_line_1,
            grid_line_2, grid_line_3,
            grid_line_4]


def draw_grid():
    # printing the grid line by line as a string
    # this is my 2D graphical engine of sorts
    for line in ttt_grid:
        ttt_row = ""
        for cell in line:
            ttt_row += cell
        print(ttt_row)

# the two players; indx0 == player sign (X, or O), inx1/2 == player grid coords
player_one = ["", 0, 0]
player_two = ["", 0, 0]


def choose_player():
    global player_one
    global player_two
    choice = input("Player one please choose X or O: ")
    if choice == "X" or choice == "x":
        player_one[0] = "X"
        player_two[0] = "O"
    else:
        player_one[0] = "O"
        player_two[0] = "X"
    print(f"Player one is {player_one[0]}")
    print(f"Player two is {player_two[0]}")


def no_more_move():
    # checking if the player grid has any empty cells left
    no_move_left = True
    for line in player_grid:
        for cell in line:
            if cell == " ":
                no_move_left = False
                return no_move_left
    return no_move_left


def player_move(player):
    global player_one
    global player_two
    while True:
        input_text_x = f"Player {player[0]}, please enter the x-coordinate of your move: "
        input_text_y = f"Player {player[0]}, please enter the y-coordinate of your move: "
        error_text = "Wrong input, please enter coords between 1 and 3"
        x, y = int(input(input_text_x)), int(input(input_text_y))
        if x < 1 or x > 3:
            print(error_text)
        elif y < 1 or y > 3:
            print(error_text)
        else:
            player[1] = x
            player[2] = y
        if valid_move(player):
            update_grid(player)
            break
        else:
            print("That move is already done, please choose a valid one.")


def valid_move(player_move):
    x, y = player_move[1] - 1, player_move[2] - 1  # remember 0 indexing
    if player_grid[x][y] == " ":
        return True
    else:
        return False


def update_grid(player_move):
    global player_grid
    global grid_line_1
    global grid_line_2
    global grid_line_3
    global ttt_grid
    x, y = player_move[1] - 1, player_move[2] - 1  # remember 0 indexing
    player_grid[x][y] = player_move[0]
    # must update this part of the grid as well in order to draw changes to the grid
    grid_line_1 = ["1", " ", "|", player_grid[0][0], "|", player_grid[0][1], "|", player_grid[0][2], "|", " ", "1"]
    grid_line_2 = ["2", " ", "|", player_grid[1][0], "|", player_grid[1][1], "|", player_grid[1][2], "|", " ", "2"]
    grid_line_3 = ["3", " ", "|", player_grid[2][0], "|", player_grid[2][1], "|", player_grid[2][2], "|", " ", "3"]
    ttt_grid = [grid_line_0, grid_line_1, grid_line_2, grid_line_3, grid_line_4]


# game logic
def player_win(player):
    win = False
    winning_case = [player[0], player[0], player[0]]
    # possible winning configurations
    win_1 = [player_grid[0][0], player_grid[0][1], player_grid[0][2]]
    win_2 = [player_grid[1][0], player_grid[1][1], player_grid[1][2]]
    win_3 = [player_grid[2][0], player_grid[2][1], player_grid[2][2]]
    win_4 = [player_grid[0][0], player_grid[1][0], player_grid[2][0]]
    win_5 = [player_grid[0][1], player_grid[1][1], player_grid[2][1]]
    win_6 = [player_grid[0][2], player_grid[1][2], player_grid[2][2]]
    win_7 = [player_grid[0][0], player_grid[1][1], player_grid[2][2]]
    win_8 = [player_grid[0][2], player_grid[1][1], player_grid[2][0]]
    winning_configurations = [win_1, win_2, win_3, win_4, win_5, win_6, win_7, win_8]
    for config in winning_configurations:
        if winning_case == config:
            win = True
            return win
    return win

# main game calls
def ttt_game():
    draw_grid()
    choose_player()
    while True:
	
        draw_grid()
		
		# let player one go
        player_move(player_one)
        if player_win(player_one):
            draw_grid()
            print(f"Player {player_one[0]} won!")
            break
        if no_more_move():
            draw_grid()
            print("It's a tie! Game is over.")
            break
        
		draw_grid()
		
        # let player two go
		player_move(player_two)
        if player_win(player_two):
            draw_grid()
            print(f"Player {player_two[0]} won!")
            break
        if no_more_move():
            draw_grid()
            print("It's a tie! Game is over.")
            break
    
	# finish
	print("Thank you for playing. Have a nice life!")


ttt_game()