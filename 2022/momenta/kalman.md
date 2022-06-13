# Kalman滤波
构建kalman滤波先验条件
- 噪声呈现高斯分布
- 构建线性变换的状态转移矩阵与观测矩阵

[kalman滤波](https://zhuanlan.zhihu.com/p/48876718)

[矩阵求导](https://blog.csdn.net/a493823882/article/details/81324037)

## 状态方程
$$x_{k+1}=Ax_{k}+Bu_{k}+\delta x$$
其中$A$表示状态转移矩阵，$B$表示控制装换矩阵, $u_k$对应控制输入信号, $\delta x$表示状态噪声，因此对应的状态方差存在如下关系：
$$P_{k+1}=AP_kA^T+Q$$
其中, $Q$表示$\delta x$高斯噪声方差


## 观测方程
$$z_k=Hx_k+\delta z$$
其中$z_k$表示观测，$H$表示观测矩阵

# 推导Kalman滤波

对系统状态按照如下约定命名
|标记|含义|对应的状态方差}
|----|----|----|
|$\widetilde{x}$|状态的最优估计|$\widetilde{P}$|
|$x'$|状态先验估计|$P'$|
|$x$|状态真值|$P$|

kalman系数用于调节系统状态，使系统状态的方差最小，即如下 
$$\widetilde{x}_{k+1}=x'_{k+1}+K(z-Hx'_{k+1})=x'_{k+1}+K(Hx+\delta z-Hx'_{k+1})\cdots(1)$$
$$\widetilde{x}_{k+1}-x=
x'_{k+1}-x+K(Hx+\delta z-Hx'_{k+1})\\
=(I-KH)(x'_{k+1}-x)+K\delta z\cdots(2)$$

$$P=(I-KH)*P'(I-KH)^T+KRK^T\cdots(3)$$
$$\frac{\partial P}{\partial K}=-2P'H^T+2K(HP'H^T+R)=0\cdots(4)$$
$$K=P'H^T(HP'H^T+R)^{-1}\cdots(5)$$
