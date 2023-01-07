---
title: Graph
author: Subhahu Jain
date: 2021-08-10
category: Data-Structure
layout: post
---

A graph is a non-linear data structure that consists of vertices (also known as nodes) and edges connecting these vertices. Here is an example of a graph class in JavaScript:

```js
class Graph {
  constructor() {
    this.vertices = new Set();
    this.edges = new Map();
  }

  addVertex(vertex) {
    this.vertices.add(vertex);
    this.edges.set(vertex, []);
  }

  addEdge(vertex1, vertex2) {
    this.edges.get(vertex1).push(vertex2);
    this.edges.get(vertex2).push(vertex1);
  }

  removeVertex(vertex) {
    this.vertices.delete(vertex);
    this.edges.delete(vertex);
    for (const adjacentVertex of this.edges.values()) {
      adjacentVertex.filter(v => v !== vertex);
    }
  }

  removeEdge(vertex1, vertex2) {
    const adjacents1 = this.edges.get(vertex1);
    const adjacents2 = this.edges.get(vertex2);
    adjacents1.splice(adjacents1.indexOf(vertex2), 1);
    adjacents2.splice(adjacents2.indexOf(vertex1), 1);
  }

  *vertices() {
    yield* this.vertices.values();
  }

  *edges() {
    for (const [vertex, adjacents] of this.edges) {
      for (const adjacent of adjacents) {
        yield [vertex, adjacent];
      }
    }
  }
}
```

To use this graph class, you can create a new instance and add vertices and edges to the graph using the addVertex and addEdge methods:

```js
const graph = new Graph();
graph.addVertex('A');
graph.addVertex('B');
graph.addVertex('C');
graph.addEdge('A', 'B');
graph.addEdge('B', 'C');
```

This creates the following graph:

A --- B
|
C

You can remove vertices and edges from the graph using the removeVertex and removeEdge methods:

```js
graph.removeVertex('B');
```

This removes the vertex B and the edges connecting it from the graph, resulting in the following graph:

A
|
C

You can iterate over the vertices and edges of the graph using the vertices and edges generators:

```js
for (const vertex of graph.vertices()) {
  console.log(vertex);
}

// Output: A C

for (const [vertex1, vertex2] of graph.edges()) {
  console.log(`${vertex1} --- ${vertex2}`);
}
// Output: A --- C
```

[1]: https://github.com/allejo/jekyll-toc
