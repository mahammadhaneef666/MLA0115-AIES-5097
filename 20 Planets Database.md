orbits(mercury, sun). 
 
 
 orbits(venus, sun).
 
 
 orbits(earth, 

orbits(moon, earth).

orbits(phobos, mars). 

orbits(deimos, mars).

planet(P) <= orbits(P, sun). 

satellite(S) <= orbits(S, P) and planet(P). 


input: orbit(moon,neptune).

ouput:false

sun). orbits(mars, sun).



**Output**



![image](https://github.com/user-attachments/assets/e2142611-73d0-40dc-8944-a6ab8fad63a9)

