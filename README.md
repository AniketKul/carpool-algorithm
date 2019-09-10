## Carpooling Algorithm

Implement a minimum matching algorithm to match riders requesting carpool in order to save total distance

**Intuition:** We create a undirected graph with riders as nodes and edges representing their shared plan. Using maximum matching with minimum weight algorithm, we can find the best sharing plan with minimum total distance

Based on Manhattan distance:
`𝑋(𝑥1, 𝑥2) and 𝑌(𝑦1, 𝑦2)`

```
𝑑(𝑋, 𝑌) = |𝑥1 − 𝑦1| + |𝑥2 − 𝑦2|
```

We define the distance between each two passengers 𝑑(𝑋, 𝑌) in five scenarios:

a. Pick up 𝑋 then pick up 𝑌 then drop off 𝑋 then drop up 𝑌: 
➢ 𝑑(𝑋𝑌) = 𝑑(1) = 𝑑(𝑋1𝑌1) + 𝑑(𝑌1𝑋2) + 𝑑(𝑋2𝑌2) 

b. Pick up 𝑋 then pick up 𝑌 then drop off 𝑌 then drop up 𝑋: 
➢ 𝑑(𝑋𝑌) = 𝑑(2) = 𝑑(𝑋1𝑌1)+ 𝑑(𝑌1𝑌2) + 𝑑(𝑌2𝑋2) 

c. Pick up 𝑌 then pick up 𝑋 then drop off 𝑋 then drop up 𝑌: 
➢ 𝑑(𝑋𝑌) = 𝑑(3) = 𝑑(𝑌1𝑋1) + 𝑑(𝑋1𝑋2) + 𝑑(𝑋2𝑌2) 

d. Pick up 𝑌 then pick up 𝑋 then drop off 𝑌 then drop up 𝑋: 
➢ 𝑑(𝑋𝑌) = 𝑑(4) = 𝑑(𝑌1𝑋1) + 𝑑(𝑋1𝑌2) + 𝑑(𝑌2𝑋2) 

d. 𝑋 and 𝑌 travels on his/her own: 
➢ 𝑑(𝑋𝑌) = 𝑑(5) = 𝑑(𝑋1𝑋2) + 𝑑(𝑌1𝑌2)

## Expected Input

- CSV file containing passenger numbers

## Expected Output

- A list of rider nodes and labels

## Level of Service

Riders are not pooling with someone if the total distance that rider spends on a shared vehicle exceeds 25% more than traveling on his/her own. We call it "level of service" to guarantee the quality of vehicle sharing.

For passenger(𝑋): 
if 𝑑(𝑋1𝑌1)+ 𝑑(𝑌1𝑋2) > 1.25𝑑(𝑌1𝑋1): 
set 𝑑(1) as +∝ 
if 𝑑(𝑋1𝑌1)+ 𝑑(𝑌1𝑌2)+ 𝑑(𝑌2𝑋2) > 1.25𝑑(𝑌1𝑋1): 
set 𝑑(2) as +∝ 
if 𝑑(𝑋1𝑌2) + 𝑑(𝑌2𝑋2) > 1.25𝑑(𝑌1𝑋1): 
set 𝑑(4) as +∝

Repeat it for all passengers and output all the distance. The weight of two passengers is defined as:

𝑑(𝑋𝑌) = min{𝑑(1), 𝑑(2), 𝑑(3), 𝑑(4), 𝑑(5)}




