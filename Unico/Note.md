# 宇研共創 
## 定翼飛機系統工程設計
###### `無人機` `飛行動力` `動態模擬`

### Modelica 模型

- AircraftDynamics
- FluidSystemComponents
- PropulsionSystem

### 名詞
Flap 襟翼 <br>
Aileron 副翼 <br>
Tnadem Wing 串翼機<br>
Rudder 方向舵 <br>
Elevator 升降舵 <br>
Spoiler 擾流板 <br>
Angle of Attack 攻角 <br>
Chord Line 弦線 <br>
Airfoil 翼型 <br>
Mean Camber Line 中弧線 <br>

### 重要數值
推力:曲線(油門)<br>
升力系數$C_l$<br>
升力系數&攻角<br>
阻力系數&攻角<br>
升阻比&攻角<br>
投影面積與攻角成正比<br>

### 公式 
$L= C_L\left({\frac1 2}\rho V^2\right)S$ <br>
L:升力 <br>
$C_L$ : 升力系數 <br>
$\rho$ : 空氣密度 <br>
$V$ : 相對於空氣的飛行速度 <br>
$S$ : 機翼投影面積 <br>
<img src="./pic/a.png" alt="drawing" width = "30%"> <br>

### 定義
機體座標系 B <br>
地球座標系 E <br>
$v = \left[u,v,w\right]^T$ <br>
$\omega = \left[p,q,r\right]^T$ <br>
攻角 $\alpha$ <br>
空速 V <br>
風軸横滾率 $P^{\left(W\right)}$ <br>
$$\alpha = \tan^{-1}\left(\omega/u\right)$$
$$V = \sqrt{u^2+v^2+w^2}$$
$$p^{\left(w\right)} = {\frac 1 V}u^T\omega$$

$\alpha_0$ : 零升力攻角 <br>
$Cl_\alpha$: 升力曲線斜度 <br>
$Cl_i$:升力系數在阻力最小位置<br>
<img src=".//Pic//Figure_3.7.png" width="50%"><br>
通常: <br>
$馬赫數M=0.2$ <br>
$雷諾數R_e=9 \times 10^6$<br>

力及力矩平衡

### 向量計算

> $若 \vec a = \{x_1,y_1\}, \vec b = \{x_2,y_2\}$
>
> $ 點積(內積) \quad \vec a \cdot \vec b = x_1 x_2 + y_1 y_2$


> $若 \vec a = \{a_1,a_2,a_3\}, \vec b = \{b_1,b_2,b_3\}$
>
> $叉積(向量積) \quad \vec a \times \vec b = (a_2 b_3 - a_3 b_2 , -a_1 b_3 + a_3 b_1 , a_1 b_2 - a_2 b_1)$

> <img src="./Pic/正射影.png" width="30%"><br>
> $正射影長度: |\vec c| = \frac {\vec a \cdot \vec b} {|\vec b |}$
>
> $正射影向量: \vec c = {\frac {\vec a \cdot \vec b} {\vec b \cdot \vec b}} \vec b, 若\vec b 為單位向量,則$
>
> $\vec c =({\vec a \cdot \vec b}) \vec b$


### AOA(攻角)


 $世界座標系: \{ x',y',z' \}$

 $機體座標系: \{ x,y,z\} , 法向量: \vec n , 各軸單位向量分別為 \{\vec u, \vec v, \vec w\}$

$飛機速度: \vec V$ 

$\vec n' 為速度 \vec V 投影至法向量 \vec n 若:$

$\vec n' \cdot \vec n > 0 則同向AOA為正,反之AOA為負 $ 

$\vec V 投影至x,y平面為向量\vec V'=(\vec V 投影至 \vec u) + (\vec V 投影至 \vec v)$




