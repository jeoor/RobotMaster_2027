# RobotMaster_2027

RoboMaster 2027 自瞄与仿真工作区：文档、规则手册和环境清单放在根仓库，两个项目以子模块引入。

## 目录

```text
.
├── docs/
│   ├── 算法优化.md
│   ├── 复刻.md
│   └── rules/                  # 官方手册（V1.0.0，20261015）
├── env/
│   └── sp-sim-linux-64.explicit.txt
├── sp_vision_25/               # 子模块
└── bevy_robomaster_simulator/  # 子模块
```

| 路径 | 内容 |
| --- | --- |
| [`sp_vision_25/`](https://github.com/jeoor/sp_vision_25) | 自瞄视觉：11 状态 EKF、条件触发的平移机动响应、自车运动补偿、几何射击窗口、仿真与消融报告 |
| [`bevy_robomaster_simulator/`](https://github.com/jeoor/bevy_robomaster_simulator) | Bevy/Avian 模拟器：Talos IPC、执行端发弹时序、敌方移动靶 AI |
| [`docs/算法优化.md`](docs/算法优化.md) | 算法优化与退化审计记录 |
| [`docs/复刻.md`](docs/复刻.md) | 本机环境复刻与构建说明 |
| [`env/sp-sim-linux-64.explicit.txt`](env/sp-sim-linux-64.explicit.txt) | Conda `sp-sim` 环境的精确锁定清单（`conda list --explicit`） |
| `docs/rules/` | 官方比赛规则、制作规范与参赛手册 |

## 获取

```sh
git clone --recurse-submodules https://github.com/jeoor/RobotMaster_2027.git
# 已克隆的话
git submodule update --init --recursive
```

## 构建与运行

```sh
cd sp_vision_25
./sim.sh build --cuda
./sim.sh run
```

`./sim.sh test` 运行自动测试，`./sim.sh report` 重跑配对消融并导出
CSV/PNG/SVG/HTML。完整环境准备与操作说明见 [`docs/复刻.md`](docs/复刻.md)；
优化审计与验证范围见 `sp_vision_25/OPTIMIZATION.md`；报告输出在
`sp_vision_25/.sim/reports/latest/index.html`（本地生成，未提交）。

## 许可证

- `sp_vision_25`：MIT，Copyright (c) 2025 TongjiSuperPower。
- `bevy_robomaster_simulator`：AGPL-3.0，上游 Blackjack200。
- 根目录文档与环境清单为项目记录，未单独声明许可证。
- `docs/rules/` 中的官方手册版权归 RoboMaster 组委会，以官方发布为准。

## 说明

- 合成观测消融与离线报告不代表渲染闭环或实车命中率。
- 模型、物理与规则参数保持上游默认，未通过修改它们制造收益。
