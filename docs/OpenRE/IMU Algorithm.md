## OpenRE IMU算法
玩过四轴，写过 IMU 的朋友可能类似的经历，IMU 算法对四轴飞行器来说至关重要，如果不加任何融合算法的条件下，仅仅靠陀螺仪积分来进行姿态解算的话，它的效果可以暂时满足四轴飞行器的飞行的，但是时间久了就会发现机身倾斜，所以 IMU 算法包的核心工作是抑制积分漂移的同时，又要满足一定的动态特性。
为了将加速度计加入进来抑制积分漂移，首先是要对加速度计的值进行滤波。STM32F1 在计算能力上有所欠缺，为了满足控制频率的要求，因此现在大多采用向量叉值误差修正陀螺仪角速度的方法。在 STM32F4 的平台上我们考虑了更大运算量的一阶扩展卡尔曼的算法。这里更多的是提供一个学习和了解的方式，相对于 PIXHAWK 等成熟飞控的多阶扩展卡尔曼滤波，效果应该是较差的，这个程序还没有在四轴飞行器上有过验证，但是通过简单测试，应该能够满足四轴飞行器的基本飞行需要。写算法的工作者能力有限，大多地方还是使用工程实践的方法，没有较为合理的理论理解，如有错误，请多包涵。

* 导航系规定

 定义不同的 XYZ 轴会导致 PITCH,ROLL,YAW 的定义不同，正负不同。
 ![Navigation System](/images/OpenRE/Navigation_System.png)

* 姿态转换矩阵

 姿态转换矩阵：参考系 n 到载体系 b(载体系 b 到参考系 n 为其转置)
 欧拉角表示：
$$
 \left[
 \begin{matrix}
   cosθcosΨ & cosθsinΨ & -sinθ \\
   sinφsinθcosΨ-cosφsinΨ & sinφsinθsinΨ+cosφcosΨ & sinφcosθ \\
   cosφsinθcosΨ+sinφsinΨ & cosφsinθsinΨ-sinφcosΨ & cosφcosθ
  \end{matrix}
  \right] 
$$

 四元数表示：
$$
 \left[
 \begin{matrix}
   q_0^2+q_1^2-q_2^2-q_3^2& 2(q_1q_2+q_0q_3)& 2(q_1q_3-q_0q_2)\\
   2(q_1q_2-q_0q_3) & q_0^2-q_1^2+q_2^2-q_3^2 & 2(q_2q_3+q_0q_1)\\
   2(q_1q_3+q_0q_2) & 2(q_2q_3-q_0q_1) & q_0^2-q_1^2-q_2^2+q_3^2
  \end{matrix}
  \right] 
$$

 算法流程图：
 ![Algorithm Flow](/images/OpenRE/Algorithm_Flow.png)

* 扩展卡尔曼滤波公式

 详见维基百科：
 https://en.wikipedia.org/wiki/Extended_Kalman_filter

 基本公式：
 $$
   \dot{x} = f(x(t),u(t))+w(t),w(t)\sim N(0,Q(t))\\
   z(k)=h(x_k)+v_k,v_k\sim N(0,R_k)
 $$
 式中：
 $$
   x_k = 
   \left[
  \begin{matrix}
   q_0\\
   q_1\\
   q_2\\
   q_3
  \end{matrix}
  \right] ~ ~ ~ ~ ~ ~ ~
  z_k=
  \left[
 \begin{matrix}
   a_x\\
   a_y\\
   a_z
  \end{matrix}
  \right] 
 $$

 推出：
 $$
 \dot{
 \left[
  \begin{matrix}
   q_0\\
   q_1\\
   q_2\\
   q_3
  \end{matrix}
  \right]
  } 
  = \left[
  \begin{matrix}
   -q_1 & -q_2 & -q_3\\
   q_0 & q_2 & -q_3\\
   q_0 & -q_1 & q_3\\
   q_0 & q_1 & -q_2
  \end{matrix}
  \right]
  \left[
  \begin{matrix}
   g_x\\
   g_y\\
   g_z
  \end{matrix}
  \right]
  +w(t)
 $$
 $$
 \left[
  \begin{matrix}
   a_x\\
   a_y\\
   a_z
  \end{matrix}
  \right]_{estimate}
  =C_n^b\left[
  \begin{matrix}
   0\\
   0\\
   G
  \end{matrix}
  \right]
  +v(t)
 $$
 $$
 \frac{\partial f}{\partial x} =  
 \left[
  \begin{matrix}
   1 & -g_x & -g_y & -g_z\\
   g_x & 1 & g_y & -g_z\\
   g_x & -g_y & 1 & g_z\\
   g_x & g_y & -g_z & 1
  \end{matrix}
  \right]
 $$
  $$
 \frac{\partial h}{\partial x} =  
 \left[
  \begin{matrix}
   -2q_2G & 2q_3G & -2q_0G & 2q_1G\\
   2q_1G & 2q_0G & 2q_3G & 2q_2G\\
   2q_0G & -2q_1G & -2q_2G & 2q_3G
  \end{matrix}
  \right]
 $$

