---
title: Dijkstra
author: Subhahu Jain
date: 2019-04-27
category: Algorithm
layout: post
---



Dijkstra's algorithm is an algorithm for finding the shortest path between two nodes in a graph. It works by repeatedly visiting the nodes in the graph, updating their distances from the starting node, and keeping track of the shortest path to each node.

Here is an example of a function that implements Dijkstra's algorithm in JavaScript:

```js
function dijkstra(graph, start, end) {
  const distances = {};
  const previous = {};
  const queue = new PriorityQueue();
  for (const vertex in graph) {
    if (vertex === start) {
      distances[vertex] = 0;
      queue.enqueue(vertex, 0);
    } else {
      distances[vertex] = Infinity;
      queue.enqueue(vertex, Infinity);
    }
    previous[vertex] = null;
  }
  while (queue.values.length > 0) {
    const current = queue.dequeue().val;
    if (current === end) {
      const path = [end];
      let lastStep = end;
      while (previous[lastStep]) {
        path.unshift(previous[lastStep]);
        lastStep = previous[lastStep];
      }
      return path;
    }
    if (current || distances[current] !== Infinity) {
      for (const neighbor in graph[current]) {
        const alternate = distances[current] + graph[current][neighbor];
        if (alternate < distances[neighbor]) {
          distances[neighbor] = alternate;
          previous[neighbor] = current;
          queue.enqueue(neighbor, alternate);
        }
      }
    }
  }
  return null;
}
```

This function takes a graph, a start node, and an end node as arguments, and returns an array representing the shortest path from the start node to the end node.

To use this function, you can define your graph as an adjacency list and pass it, along with the start node and the end node, as arguments to the function:

```js
const graph = {
  a: { c: 1, d: 4, e: 3 },
  b: { a: 2, d: 4 },
  c: { b: 2, d: 4, e: 3 },
  d: { e: 1 },
  e: {}
};

const start = 'a';
const end = 'e';
const path = dijkstra(graph, start, end);  // path = ['a', 'e']
```

This function returns the shortest path from the start node