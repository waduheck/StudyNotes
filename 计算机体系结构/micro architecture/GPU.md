不太懂：
1. SIMD、SIMT、SPMD之间的关系


![[Pasted image 20231223232733.png]]
## MMX操作
![[Pasted image 20231222155420.png]]

![[Pasted image 20231222155535.png]]

![[Pasted image 20231222155558.png]]


threads 与 warp
![[Pasted image 20231222162323.png]]

![[Pasted image 20231223214537.png]]

利用掩码解决分支问题，执行到该层时通过掩码决定实不实行
![[Pasted image 20231223233704.png]]

将同一代码的warp进行合并
![[Pasted image 20231223234018.png]]