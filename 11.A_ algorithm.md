from queue import PriorityQueue class Graph: def **init**(self): self.graph = {}

def add\_edge(self, node, neighbors):  ![](Aspose.Words.6c1ee484-4cb3-4bdf-a099-902d8f1b0376.001.png)   self.graph[node] = neighbors

def astar(graph, start, goal): visited = set() priority\_queue = PriorityQueue() priority\_queue.put((0, start, []))

while not priority\_queue.empty(): ![](Aspose.Words.6c1ee484-4cb3-4bdf-a099-902d8f1b0376.002.png)

`    `current\_cost, current\_node, path = priority\_queue.get() 

`    `if current\_node in visited:         continue 

visited.add(current\_node) path = path + [current\_node] 

`    `if current\_node == goal:         return path 

`    `for neighbor, cost in graph.graph[current\_node].items(): 

`        `if neighbor not in visited: 

`            `priority\_queue.put((current\_cost + cost + heuristic(neighbor, goal), neighbor, path)) 

return None

def heuristic(node, goal):

x1, y1 = node ![](Aspose.Words.6c1ee484-4cb3-4bdf-a099-902d8f1b0376.003.png)

x2, y2 = goal 

return ((x1 - x2) \*\* 2 + (y1 - y2) \*\* 2) \*\* 0.5

g = Graph() g.add\_edge((0, 0), {(0, 1): 1, (1, 0): 1}) g.add\_edge((0, 1), {(0, 0): 1, (1, 1): 1}) g.add\_edge((1, 0), {(0, 0): 1, (1, 1): 1}) g.add\_edge((1, 1), {(0, 1): 1, (1, 0): 1})

start\_node = (0, 0) goal\_node = (1, 1) path = astar(g, start\_node, goal\_node) if path: print("Shortest Path:", path) else: print("No path found.")

**output**
![a algorithm](https://github.com/user-attachments/assets/cc34f6be-9857-4c76-9828-c6d4e45a14b7)
