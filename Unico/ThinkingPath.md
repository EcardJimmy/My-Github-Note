# Concept & Thinking
## [固定翼無人機:](./UAVModel/FixedWingDrone.mo)
### 重力,地球座標
- [機身座標與地球座標轉換](./UAVModel/CoordinateTransformation.mo)

### 機體Package: 重心,重量,機體座標
- 機身 Fuselage
- 前翼 FrontWing
    - 左襟翼 Flap: 角度
    - 右襟翼 Flap: 角度
- 後翼 RealWing
    - 左襟翼 Flap: 角度
    - 右襟翼 Flap: 角度
    - 垂直翼 
        - 左方向舵 Rudder: 角度
        - 右方向舵 Rudder: 角度
- 引擎 Engine
    - 葉片 Propeller: 轉速,推力
- 起落架 LandingGear
    - 前起落架
    - 後起落架
### 參數
### 變數
- Thrust
- 升力系數 $C_L$
- 阻力系數 $C_D$
- 攻角 Angle of Attack
- 飛行速度
### 力和扭距Package
- 推力
    - 油門與推力曲線
    - 油門與轉速曲線
- 升力
    - 升力系數與攻角曲線
- 阻力
    - 阻力系數與攻角曲線
### 控制Package
- 起飛控制
- 降落控制
- 巡航控制
- 前行控制
- 上升控制
- 轉彎控制
### 環境Package
- 空氣密度
- 風向,風力
### Interface Package
### Functions Package
### Sensors Package
- Pitch
- Roll
- Yaw
### Icons Package
### Units Package