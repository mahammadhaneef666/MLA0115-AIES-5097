# 8-PUZZLE

# PROGRAM::

      from queue import PriorityQueue

     goal_state = [[1, 2, 3], [4, 5, 6], [7, 8, 0]]

     moves = {
    0: [(1, 0), (0, 1)],      # Down, Right
    1: [(1, 0), (0, -1), (0, 1)], # Down, Left, Right
    2: [(1, 0), (0, -1)],     # Down, Left
    3: [(0, 1), (1, 0)],      # Right, Down
    4: [(0, -1), (0, 1), (1, 0)], # Left, Right, Down
    5: [(0, -1), (1, 0)],     # Left, Down
    6: [(0, 1), (-1, 0)],     # Right, Up
    7: [(0, -1), (0, 1), (-1, 0)], # Left, Right, Up
    8: [(0, -1), (-1, 0)]     # Left, Up
    }

    def heuristic(state):
    distance = 0
    for i in range(3):
        for j in range(3):
            if state[i][j] != 0:
                x, y = divmod(state[i][j] - 1, 3)
                distance += abs(x - i) + abs(y - j)
    return distance

    def astar_search(initial_state):
    frontier = PriorityQueue()
    frontier.put(tuple(map(tuple, initial_state)), 0)
    came_from = {}
    cost_so_far = {}
    
    came_from[tuple(map(tuple, initial_state))] = None
    cost_so_far[tuple(map(tuple, initial_state))] = 0

    while not frontier.empty():
        current = frontier.get()

        if current == tuple(map(tuple, goal_state)):
            break

        zero_i, zero_j = next((i, j) for i in range(3) for j in range(3) if current[i][j] == 0)

        for move in moves[zero_i * 3 + zero_j]:
            next_i = zero_i + move[0]
            next_j = zero_j + move[1]

            if not (0 <= next_i < 3 and 0 <= next_j < 3):
                continue

            next_state = [list(row) for row in current]  
            next_state[zero_i][zero_j], next_state[next_i][next_j] = next_state[next_i][next_j], next_state[zero_i][zero_j]
            next_state_tuple = tuple(map(tuple, next_state))

            new_cost = cost_so_far[current] + 1
            if next_state_tuple not in cost_so_far or new_cost < cost_so_far[next_state_tuple]:
                cost_so_far[next_state_tuple] = new_cost
                priority = new_cost + heuristic(next_state)
                frontier.put(next_state_tuple, priority)
                came_from[next_state_tuple] = current

     return came_from, cost_so_far[tuple(map(tuple, goal_state))]

     initial_state = [[1, 2, 3], [4, 0, 6], [7, 5, 8]]
     came_from, cost = astar_search(initial_state)

    def reconstruct_path(came_from, start, goal):
    current = goal
    path = [current]
    while current != start:
        current = came_from[current]
        path.append(current)
      path.reverse()
       return path

       solution_path = reconstruct_path(came_from,
                                  tuple(map(tuple, initial_state)),
                                  tuple(map(tuple, goal_state)))

     print("Initial state:", initial_state)
    print("Goal state:", goal_state)
     print("Solution path:")
     for state in solution_path:
       print([list(row) for row in state])
      print("Total cost:", cost)

# OUTPUT::

![8Puzzle](https://github.com/user-attachments/assets/737d3e85-7a55-4b9f-b06f-3df89c7169c5)
