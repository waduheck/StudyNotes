![[Pasted image 20231226092128.png]]
![[Pasted image 20231226092226.png]]
![[Pasted image 20231226092504.png]]

![[Pasted image 20231226092607.png]]

![[Pasted image 20231226093359.png]]

![[Pasted image 20231226100621.png]]

![[Pasted image 20231226100822.png]]

![[Pasted image 20231226100952.png]]

## 几种gpu架构
![[Pasted image 20231226101353.png]]
![[Pasted image 20231226101426.png]]
![[Pasted image 20231226101445.png]]

## memory access
### latency hiding
![[Pasted image 20231226101808.png]]

### 内存合并
**目的**：

- 当访问全局内存时，我们希望确保并行运行的线程访问临近的内存位置。这样可以最大化带宽利用率，因为物理内存的读写通常是以缓存行为单位进行的。

**优化**：

- 如果一个线程束（在CUDA中称为“warp”，通常包含32个线程）中的所有线程同时访问一个缓存行内的数据，则可以一次性通过一个内存事务来满足所有线程的数据需求。

**合并访问**：

- 合并访问（Coalesced Access）意味着线程束中的线程访问连续的内存地址，这样它们就能共享同一个内存读写事务。
![[Pasted image 20231226102620.png]]
![[Pasted image 20231226102633.png]]