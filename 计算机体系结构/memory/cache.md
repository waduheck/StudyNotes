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
![[Pasted image 20231225105046.png]]


![[Pasted image 20231225104910.png]]
![[Pasted image 20231225105323.png]]


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