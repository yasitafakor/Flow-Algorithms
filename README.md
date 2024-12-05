# Flow Algorithms for Network Optimization

This repository implements three different algorithms for solving the **Maximum Flow** problem in a flow network: **Cycle Canceling**, **Successive Shortest Path**, and **Capacity Scaling**. These algorithms are fundamental in network flow analysis, and they are designed to compute the maximum flow in a flow network, given certain constraints on capacities and flow.

## Algorithms Implemented

### 1. **Cycle Canceling Algorithm**
The Cycle Canceling algorithm is an approach for solving the **Maximum Flow** problem using residual graphs. The idea is to find and cancel cycles in the residual graph to improve the flow until no more augmenting paths exist. This algorithm uses **Depth First Search (DFS)** to explore the graph and **Ford-Fulkerson method** to compute the maximum flow.

#### Key Concepts:
- **DFS**: A graph traversal method that explores as far as possible along each branch before backtracking.
- **Ford-Fulkerson**: A method for computing the maximum flow in a flow network by repeatedly finding augmenting paths.

#### How It Works:
- The algorithm starts by copying the input graph into a residual graph.
- Using DFS, it finds augmenting paths in the residual graph.
- For each found path, it calculates the minimum capacity (path flow) and updates the residual graph by subtracting the path flow from the capacities.
- This process repeats until no more augmenting paths can be found.
  
#### Time Complexity:
- \( O(n^2U) \), where \( n \) is the number of vertices and \( U \) is the upper bound on edge capacities.

### 2. **Successive Shortest Path Algorithm**
The **Successive Shortest Path** algorithm is used to solve the **minimum-cost flow** problem, where the objective is to send as much flow as possible from the source to the sink while minimizing the total cost. It employs shortest path algorithms, like **Dijkstra** or **Bellman-Ford**, to repeatedly find the shortest path with respect to reduced costs.

#### Key Concepts:
- **Reduced Cost**: A cost transformation used to simplify the pathfinding process and reduce the overall computational complexity.
- **Shortest Path**: The algorithm iteratively finds the shortest path from the source to the sink using reduced costs.

#### How It Works:
- Initially, the graph is set up with nodes and edges, and balances are calculated for each vertex.
- Using **Dijkstra’s algorithm**, the shortest path is found, and the flow along this path is updated.
- The algorithm proceeds to find additional paths while adjusting the flow and costs.
- A special "dummy source" and "dummy sink" are added to manage the flow across the graph more efficiently.

### 3. **Capacity Scaling Algorithm**
The **Capacity Scaling** algorithm is another approach to solving the **Maximum Flow** problem. It works by progressively scaling down the network’s edge capacities to find augmenting paths, starting with the largest possible capacity and gradually reducing the capacity as the algorithm proceeds.

#### Key Concepts:
- **Capacity Scaling**: This method uses a scaling factor `delta`, which is initially set to 1 and gradually doubled until it reaches the maximum edge capacity.
- **Residual Network**: The residual network is updated as the flow is augmented along the paths.

#### How It Works:
- The algorithm begins by identifying the largest edge capacity in the graph and sets `delta` to 1.
- The main loop continues to find paths using **findPath(delta)** until `delta` becomes zero.
- For each found path, the flow is adjusted, and the residual network is updated.
- The total flow cost is computed and printed after all paths have been processed.

#### Time Complexity:
- Typically faster than other flow algorithms for large networks due to its focus on high-capacity edges first.

## Features

- **Cycle Canceling**: Uses DFS and Ford-Fulkerson to find the maximum flow in a network.
- **Successive Shortest Path**: Uses Dijkstra's algorithm to find minimum-cost flows.
- **Capacity Scaling**: Efficiently computes the maximum flow by scaling edge capacities.
