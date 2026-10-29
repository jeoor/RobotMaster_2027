# RobotMaster_2027

RoboMaster 2027 自瞄与仿真工作区：根目录保存算法记录、环境说明和试验数据，两个项目以子模块引入。

## 目录

| 路径 | 内容 |
| --- | --- |
| [`sp_vision_25/`](https://github.com/jeoor/sp_vision_25) | 自瞄视觉：11 状态 EKF、条件触发的平移机动响应、自车运动补偿、几何射击窗口、仿真与消融报告 |
| [`bevy_robomaster_simulator/`](https://github.com/jeoor/bevy_robomaster_simulator) | Bevy/Avian 模拟器：Talos IPC、执行端发弹时序、敌方移动靶 AI |
| `算法优化.md` | 算法优化与退化审计记录 |
| `复刻.md` | 本机环境复刻与构建说明 |
| `batch_*.json` | 模拟器批量射击试验结果 |
| `sp-sim-linux-64.explicit.txt` | Conda 环境显式包列表 |
| `RoboMaster 2027 ... .pdf` | 官方比赛规则、制作规范与参赛手册 |

## 获取

```sh
git clone --recurse-submodules https://github.com/jeoor/RobotMaster_2027.git
# 已克隆的话
git submodule update --init --recursive
```

## 构建与验证

```sh
cd sp_vision_25
./sim.sh build
./sim.sh test
./sim.sh report
./sim.sh run
```

优化审计与验证范围见 `sp_vision_25/OPTIMIZATION.md`；报告输出在
`sp_vision_25/.sim/reports/latest/index.html`（本地生成，未提交）。

## 说明

- 合成观测消融与离线报告不代表渲染闭环或实车命中率。
- 模型、物理与规则参数保持上游默认，未通过修改它们制造收益。
