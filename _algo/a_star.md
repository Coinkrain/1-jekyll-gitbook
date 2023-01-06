---
title: A*
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---


The A* (A-star) algorithm is a graph search algorithm that is used to find the shortest path between two points in a graph. It is an extension of the Dijkstra's algorithm and uses a heuristic function to estimate the distance between the two points. The heuristic function should be an underestimate of the actual distance, so that the algorithm is guaranteed to find the shortest path.

Here is an example of how to implement the A* algorithm in JavaScript:

```js
function AStar(start, end, graph) {
  // Set of nodes already evaluated
  let closedSet = new Set();
  // Set of currently discovered nodes that are not evaluated yet.
  // Initially, only the start node is known.
  let openSet = new Set();
  openSet.add(start);
  // For each node, which node it can most efficiently be reached from.
  // If a node can be reached from many nodes, cameFrom will eventually contain the
  // most efficient previous step.
  let cameFrom = new Map();
  // For each node, the cost of getting from the start node to that node.
  let gScore = new Map();
  // The cost of going from start to start is zero.
  gScore.set(start, 0);
  // For each node, the total cost of getting from the start node to the goal
  // by passing by that node. That value is partly known, partly heuristic.
  let fScore = new Map();
  // For the first node, that value is completely heuristic.
  fScore.set(start, graph.heuristicCostEstimate(start, end));

  while (openSet.size > 0) {
    // The node in openSet having the lowest fScore[] value
    let current = null;
    for (let node of openSet) {
      if (current === null || fScore.get(node) < fScore.get(current)) {
        current = node;
      }
    }

    if (current === end) {
      return reconstructPath(cameFrom, end);
    }

    openSet.delete(current);
    closedSet.add(current);

    for (let neighbor of graph.neighbors(current)) {
      if (closedSet.has(neighbor)) {
        continue;
      }

      // The distance from start to a neighbor
      let tentativeGScore = gScore.get(current) + graph.cost(current, neighbor);

      if (!openSet.has(neighbor)) {
        openSet.add(neighbor);
      } else if (tentativeGScore >= gScore.get(neighbor)) {
        continue;
      }

      // This path is the best until now. Record it!
      cameFrom.set(neighbor, current);
      gScore.set(neighbor, tentativeGScore);
      fScore.set(neighbor, gScore.get(neighbor) + graph.heuristicCostEstimate(neighbor, end));
    }
  }

  return null;
}

function reconstructPath(cameFrom, current) {
  let totalPath = [current];
  while (cameFrom.has(current)) {
    current = cameFrom.get(current);
    totalPath.unshift(current);
  }
  return totalPath;
}
```

Here are the methods of the A* (A-star) algorithm that are implemented in the above code:

 - `AStar(start, end, graph)`: This is the main function that performs the A* search. It takes three arguments: the start node, the end node, and a graph object. The function returns the shortest path from the start node to the end node, or `null` if no path is found.

 - `reconstructPath(cameFrom, current)`: This function is used to reconstruct the shortest path from the start node to the end node once the search is complete. It takes two arguments: `cameFrom`, which is a map that contains the most efficient previous step for each node, and `current`, which is the current node being processed. The function returns an array of nodes representing the shortest path from the start node to the end node.