

## 拓扑排序
拓扑排序是针对有向无环图（DAG）的一种排序方法，其目的是将图中的所有顶点排成一个线性序列，使得对于图中的每一条有向边 \( uv \)（从顶点 \( u \) 指向顶点 \( v \)），顶点 \( u \) 都在顶点 \( v \) 之前。换句话说，如果顶点 \( v \) 依赖于顶点 \( u \)，那么 \( u \) 必须在排序中出现在 \( v \) 之前。

进行拓扑排序的一个常见算法是使用深度优先搜索（DFS），但更常用的是利用入度（指向顶点的边的数量）的概念进行排序。以下是基于入度的拓扑排序算法的步骤：

1. **计算每个顶点的入度**：对于图中的每个顶点，计算有多少条边指向它。

2. **初始化队列**：创建一个队列，用于存放所有入度为0的顶点。入度为0意味着没有其他顶点指向它，这样的顶点可以作为拓扑排序的起点。

3. **进行排序**：
   - 当队列非空时，从队列中移除一个入度为0的顶点，并将其添加到拓扑排序的结果中。
   - 遍历该顶点的所有邻接点，将这些邻接点的入度减1（因为移除了一个指向它们的边）。如果任何邻接点的入度变为0，则将这个邻接点加入队列中。

4. **检查是否存在环**：如果排序完成后，排序中的顶点数量少于图中的顶点总数，这意味着图中存在环，因为至少有一个顶点的入度永远不会变为0。

5. **输出结果**：如果图中不存在环，则排序的结果是图的一个有效的拓扑排序。

这种基于入度的拓扑排序算法简单且直观，适用于大多数需要拓扑排序的场景。

## SPT
无需使用PQ来储存顶点，只需按拓扑顺序进行访问即可
![[Pasted image 20231216134730.png]]

## 最小递增子序列
![[Pasted image 20231216144924.png]]