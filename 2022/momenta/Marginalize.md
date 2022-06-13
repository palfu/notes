
## Marginalize
我们知道SLAM中的图优化和BA都是最小二乘问题，通过高斯牛顿迭代求得，即
其中，，J是误差对位姿等的雅克比，W是权重。我们关注的Marginalize. 就是说只去求解我们希望保留的变量，那些我们要marg的变量就不关心了，从而达到减少计算的目的。假设变量x中可以分为保留部分和marg部分，那么上面的线性方程可以写成如下形式：
$$
\left[
\begin{matrix}
\Lambda_a& \Lambda_b \\
\Lambda_c& \Lambda_d
\end{matrix}
\right]
\left[
\begin{matrix}
\delta_a \\
 \delta_b
\end{matrix}
\right]
=\left[
\begin{matrix}
g_a \\
g_b
\end{matrix}\right]
$$

通过消元法可以消除$\delta_a$，得到如下公式
$$
\left[
\begin{matrix}
\Lambda_c& \Lambda_c\Lambda_a^{-1}\Lambda_b \\
\Lambda_c& \Lambda_d
\end{matrix}
\right]
\left[
\begin{matrix}
\delta_a \\
 \delta_b
\end{matrix}
\right]
=\left[
\begin{matrix}
\Lambda_c\Lambda_a^{-1}g_a \\
g_b
\end{matrix}\right]
$$
$$
\left[
\begin{matrix}
0 & \Lambda_d-\Lambda_c\Lambda_a^{-1}\Lambda_b
\end{matrix}
\right]
\left[
\begin{matrix}
\delta_a \\
 \delta_b
\end{matrix}
\right]
=\begin{matrix}
g_b-\Lambda_c\Lambda_a^{-1}g_a
\end{matrix}
$$

这里$\Lambda_c\Lambda_a^{-1}\Lambda_b$就称为$\Lambda_a$在$\Lambda_c$中的舒尔补。这样我们就能够迭代的更新部分变量，从而维持计算量不增加。在上面这个过程中，我们要注意，构建出来的Hx=b是利用了marg变量的信息，也就是说我们没有人为的丢弃约束，所以不会丢失信息，但是计算结果的时候，我们只去更新了我们希望保留的那些变量的值。在slam的过程中，BA不断地加入新的待优化的变量，并marg旧的变量，从而使得计算量维持在一定水平
