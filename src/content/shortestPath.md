---
type: algorithm
solverKey: shortestPath
friendlyName: Shortest Path
class: heuristic
defaults:
  evaluatingDetailLevel: 1
  maxEvaluatingDetailLevel: 1
---


# Shortest Path

This is a heuristic, greedy algorithm. It continually chooses the best looking option from the current state.

  1. From the starting point
  2. sort the remaining available points based on cost (distance)
  3. Choose the closest point and go there
  4. Chosen point is no longer an "available point"
  5. Continue this way until there are no available points, and then return to the start.


## The code

```javascript
const shortestPath = async points => {
  const path = [points.shift()];

  while (points.length > 0) {
    // sort remaining points in place by their 
    // distance from the last point in the current path
    points.sort((a, b) => (
      distance(path[path.length - 1], b) -
      distance(path[path.length - 1], a)
    ));

    // go to the closest remaining point
    path.push(points.pop());
  }

  // return to start after visiting all other points
  path.push(path[0]);
  const cost = pathCost(path);
}
```
