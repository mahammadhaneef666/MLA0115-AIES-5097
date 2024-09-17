# WATER_JUG_PROBLEM

# PROBLEM::

    from collections import deque

    def water_jug_problem(capacity_a, capacity_b, target):
      visited = set()
    queue = deque()
    queue.append((0, 0, []))
    
    while queue:
        a, b, steps = queue.popleft()
        
        if a == target or b == target or a + b == target:
            steps.append((a, b))
            return steps
        
        if (a, b) in visited:
            continue
        visited.add((a, b))
        
        possible_states = [
            (capacity_a, b),
            (a, capacity_b),
            (0, b),
            (a, 0),
            (a - min(a, capacity_b - b), b + min(a, capacity_b - b)),
            (a + min(b, capacity_a - a), b - min(b, capacity_a - a))
        ]
        
        actions = [
            f"Fill Jug A to {capacity_a}",
            f"Fill Jug B to {capacity_b}",
            "Empty Jug A",
            "Empty Jug B",
            f"Pour Jug A into Jug B",
            f"Pour Jug B into Jug A"
        ]
        
        for i, state in enumerate(possible_states):
            if state not in visited:
                new_steps = steps + [(a, b)]
                queue.append((state[0], state[1], new_steps))

    return None

    capacity_a = 4  
    capacity_b = 3
    target = 2

    result = water_jug_problem(capacity_a, capacity_b, target)

    if result:
    print(f"It is possible to measure {target} liters using the jugs.")
    print("Steps to reach the goal:")
    for step in result:
        print(f"Jug A: {step[0]}, Jug B: {step[1]}")
    else:
    print(f"It is not possible to measure {target} liters using the jugs.")

# OUTPUT::

![A(star)](https://github.com/user-attachments/assets/90b5aac1-179f-4a57-8c2c-6d85f2f900c0)
