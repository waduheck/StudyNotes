## improving
![[a6f06f29ef76f118e2036b31d4d982fd_720.png]]
![[Pasted image 20231225105610.png]]
这张PPT幻灯片介绍了一些提高基本缓存性能的方法，主要分为两类：减少缓存未命中率（miss rate）和减少缓存未命中的延迟或成本（miss latency/cost）。

### 减少缓存未命中率

1. **增加相联度（More associativity）**：
   - 相联度是缓存中一组中能够存储多少个缓存行的度量。增加相联度可以减少缓存冲突，因为每个缓存行有更多的位置可供选择。

2. **相联度的替代方案/增强（Alternatives/enhancements to associativity）**：
   - 包括“牺牲缓存”（victim caches）、哈希（hashing）、伪相联（pseudo-associativity）、偏斜相联（skewed associativity）等技术，这些技术可以减少缓存冲突和提高缓存的有效性。

3. **更好的替换/插入策略（Better replacement/insertion policies）**：
   - 这些策略决定哪个缓存行被替换。有效的策略可以减少缓存未命中，如最近最少使用（LRU）策略。

4. **软件方法（Software approaches）**：
   - 优化程序的访存模式，如循环变换和数据预取，以减少缓存未命中。
   - ![[5e4402d6b137826b07eb9835f48f7a20_720.png]]
   - ![[9608f5c1cab9820ff06b90385ff22a39_720.png]]
   - ![[5aa803b808425db18f4c21192b26dca7_720.png]]
   - ![[a250b737a82e7572461d53b248bea3e2 1.png]]
#### Blocking（块划分）

**定义**：
- 这种技术涉及将操作数组的循环分解成较小的计算块，这样每个块的数据就能够完全或部分地存放在缓存中。

**目的**：
- 通过这种方式，可以减少缓存冲突，因为每次计算只处理一小部分数据，并且这部分数据可以保持在缓存中，直到计算完成。
- 它使得处理器在执行循环计算时能更高效地访问数据，因为数据更有可能在缓存中找到（缓存命中），而不是在主内存中（缓存未命中）。

**原理**：
- 每个计算块的大小是根据缓存的大小精心选择的，以确保它们能够适合缓存。这样做可以最大限度地减少因为缓存不命中导致的数据重新加载。

#### Tiling（平铺）

**定义**：
- “Tiling”是Blocking的另一个术语，通常用于矩阵乘法等二维数组操作。

**目的**：
- 这样的数据结构和算法优化允许程序在内存中按照“瓷砖”或“块”的形式工作，这些“瓷砖”或“块”代表原始数据的子集。
- 这种方法可以提高数据局部性，因为它减少了每次计算所需的数据量，并确保这些数据可以一次性加载到缓存中。

### 与之前讨论的缓存优化技术的联系

Blocking和Tiling直接关联到之前讨论的缓存优化方法，特别是与子块/分区方法相联系。通过分割循环和数据结构，Blocking和Tiling实现了类似于子块/分区的效果，但在软件层面上。它们通过控制程序的数据访问模式来优化缓存的使用，而子块/分区则是通过硬件结构的改变来达到相似的效果。

这些方法的共同目标是减少缓存未命中的次数（提高缓存命中率），减少因访问主内存而产生的延迟，从而提高程序的整体性能。通过将数据访问模式与缓存架构相适应，可以显著提高数据访问的效率。
### 减少缓存未命中的延迟或成本

1. **多级缓存（Multi-level caches）**：
   - 使用多个缓存级别，如L1、L2、L3等，以减少主存访问的次数。

2. **首先获取关键字（Critical word first）**：
   - 当请求缓存行时，首先提供所需的特定数据字，而不是等待整个缓存行装载完成。

3. **子块/分区（Subblocking/sectoring）**：
   - 将缓存行分为更小的单元，可以减少在每次缓存未命中时需要传输的数据量。

4. **更好的替换/插入策略（Better replacement/insertion policies）**：
   - 与上文相同，有效的缓存替换策略不仅可以减少未命中率，也可以减少由于缓存未命中引起的延迟。

5. **非阻塞缓存（Non-blocking caches）**：
   - 允许在处理缓存未命中时继续进行其他缓存访问，可以并行处理多个缓存未命中。

6. **每周期多次访问（Multiple accesses per cycle）**：
   - 增加缓存带宽，允许每个时钟周期处理更多的内存访问。

7. **软件方法（Software approaches）**：
   - 优化代码，减少延迟影响，如软件预取和缓存亲和性调度。

总的来说，这张PPT强调了为了提高缓存性能，我们需要从减少缓存未命中和减少未命中成本两个方面入手。这可以通过硬件改进和软件优化来实现。

##
![[Pasted image 20231224163848.png]]


## direct-map
![[Pasted image 20231224165639.png]]

![[Pasted image 20231224165802.png]]

## Set Associativity
![[Pasted image 20231224170131.png]]

## full associate
![[Pasted image 20231224170257.png]]

## remote memory
![[Pasted image 20231224191721.png]]

## issues
1. 不同core的l1缓存之间的一致性
2. 
## Subblocked
![[Pasted image 20231224200345.png]]

## 指令与数据separate or unified
![[Pasted image 20231224200559.png]]
![[Pasted image 20231224200840.png]]

![[Pasted image 20231224200946.png]]


![[Pasted image 20231224202532.png]]
paralle 与 isolated之间减少latency的方法

## 缓存管理机制
1. **Belady's OPT Replacement**：也被称为最佳替换策略，它可以预知未来的访问模式，并总是淘汰那些在未来最长时间内不会被访问的缓存页。在这个例子中，有四次缓存未命中（M），导致四次停顿（stalls）。
    
2. **MLP-Aware Replacement**：这是一种考虑到内存级并行（MLP）的替换策略。它尝试通过并行处理缓存未命中来减少延迟的影响。在这个例子中，虽然有六次缓存未命中，但只有两次停顿，因为一些缓存未命中是并行处理的，这减少了由于缓存未命中而造成的总体延迟。
![[Pasted image 20231225105046.png]]
![[Pasted image 20231225104910.png]]
![[Pasted image 20231225105323.png]]
##

![[Pasted image 20231225103421.png]]
减少latency的方法
## MLP
![[Pasted image 20231225104548.png]]这张PPT幻灯片讲述了“Memory Level Parallelism (MLP)”的概念。MLP是在计算机执行指令时，同时生成和处理多个内存访问请求的能力。这里提到的“内存访问”通常指的是对内存的读写操作，而MLP允许这些操作并行发生，以提高执行效率。

幻灯片上展示了两种情况：

1. **Isolated Miss**: 这表示一个单独的缓存未命中事件。在这个时间点，一个数据项没有在缓存中找到，因此需要从更低级的缓存或主内存中取出数据。在"A"的时间段内，没有其他内存访问并行发生。

2. **Parallel Miss**: 这表示同时发生了多个缓存未命中事件。在"B"和"C"的时间段内，可以看到两个内存访问事件是重叠的，它们并行发生，这表明在处理一个内存未命中的同时，另一个内存未命中也在被处理。这种并行处理可以减少总的等待时间，因为不需要一个接一个地处理这些事件。

幻灯片下方的文本提到了几个关键点：

- **MLP是一个概念**，用于生成和服务多个内存访问在并行中。
- **改进MLP的技术**，例如乱序执行。乱序执行允许处理器执行非连续的指令，以此来填充由于等待内存访问完成而产生的时间间隙。
- **MLP的程度是变化的**。有些内存未命中事件是孤立的，而有些则可以并行处理。

简而言之，MLP是一个衡量处理器在内存访问方面并行能力的指标，它可以显著影响程序的执行效率。通过允许多个内存访问同时进行，处理器可以更好地利用其资源，减少因等待内存访问完成而造成的时间浪费。

## multi-core shared issues
### cache带来的冲突
![[Pasted image 20231225111359.png]]
需要改进cache的调度算法来避免

### 缓存一致性
![[Pasted image 20231225111648.png]]

解决办法
![[Pasted image 20231225111813.png]]

![[Pasted image 20231225112125.png]]

## prefetch
![[Pasted image 20231225113646.png]]
![[Pasted image 20231225114519.png]]
![[Pasted image 20231225115320.png]]
![[Pasted image 20231225114712.png]]


![[Pasted image 20231225114646.png]]

### stride prefetcher
![[Pasted image 20231225115345.png]]

![[Pasted image 20231225115358.png]]

![[Pasted image 20231225115420.png]]

![[Pasted image 20231225115254.png]]
### 预执行
![[Pasted image 20231225141558.png]]


OoO中的实际例子
![[Pasted image 20231225142208.png]]