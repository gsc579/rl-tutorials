[EN](./README.md)|中文

## JoyRL

JoyRL是一套主要基于Torch的强化学习开源框架，旨在让读者仅仅只需通过调参数的傻瓜式操作就能训练强化学习相关项目，从而远离繁琐的代码操作，并配有详细的注释以兼具帮助初学者入门的作用。

本项目为JoyRL离线版，支持读者更方便的学习和自定义算法代码，同时配备[JoyRL上线版](https://github.com/datawhalechina/joyrl)，集成度相对更高。

## 安装说明

目前支持Python 3.7和Gym 0.25.2版本。

创建Conda环境（需先安装Anaconda）
```bash
conda create -n joyrl python=3.7
conda activate joyrl
pip install -r requirements.txt
```
安装Torch：

```bash
# CPU
conda install pytorch==1.10.0 torchvision==0.11.0 torchaudio==0.10.0 cpuonly -c pytorch
# GPU
conda install pytorch==1.10.0 torchvision==0.11.0 torchaudio==0.10.0 cudatoolkit=11.3 -c pytorch -c conda-forge
# GPU镜像安装
pip install torch==1.10.0+cu113 torchvision==0.11.0+cu113 torchaudio==0.10.0 --extra-index-url https://download.pytorch.org/whl/cu113
```
## 使用说明

直接更改 `config.config.GeneralConfig()`类中的参数比如环境名称(env_name)、算法名称(algo_name)等等，然后执行:
```bash
python main.py
```
运行之后会在目录下自动生成 `tasks`文件夹用于保存模型和结果。

或者也可以新建一个`yaml`文件自定义参数，例如 `config/custom_config_Train.yaml`然后执行:
```bash
python main.py --yaml config/custom_config_Train.yaml
```
在[presets](./presets/)文件夹中已经有一些预设的`yaml`文件，并且相应地在[benchmarks](./benchmarks/)文件夹中保存了一些已经训练好的结果。

## 说明文档

请跳转[Docs](./docs/README.md)

## 环境说明

请跳转[envs](./envs/README.md)查看说明

## 算法列表

|  算法类别   |    算法名称     | Policy |                           参考文献                           |                     作者                      | 备注 |
| :-------------: | :----------------------------------------------------------: | :--: | --------------- | --------------- | --------------- |
| Value-based | [Monte Carlo](./algos/MonteCarlo/) | On | [RL introduction](https://web.stanford.edu/class/psych209/Readings/SuttonBartoIPRLBook2ndEd.pdf) | [johnjim0816](https://github.com/johnjim0816) |  |
|  | [Value Iteration](./algos/VI/) |  | [RL introduction](https://web.stanford.edu/class/psych209/Readings/SuttonBartoIPRLBook2ndEd.pdf) | [guoshicheng](https://github.com/gsc579) |  |
|  | [Q-learning](./algos/QLearning/) | Off | [RL introduction](https://web.stanford.edu/class/psych209/Readings/SuttonBartoIPRLBook2ndEd.pdf) | [johnjim0816](https://github.com/johnjim0816) |       |
|  | [Sarsa](./algos/Sarsa/) | On | [RL introduction](https://web.stanford.edu/class/psych209/Readings/SuttonBartoIPRLBook2ndEd.pdf) | [johnjim0816](https://github.com/johnjim0816) |       |
|  | [DQN](./algos/DQN/) | Off | [DQN Paper](https://www.cs.toronto.edu/~vmnih/docs/dqn.pdf) | [johnjim0816](https://github.com/johnjim0816), [guoshicheng](https://github.com/gsc579) [(CNN)](./algos/DQN/) |       |
|  | [DoubleDQN](./algos/DoubleDQN/) | Off | [DoubleDQN Paper](https://arxiv.org/abs/1509.06461) | [johnjim0816](https://github.com/johnjim0816) |       |
|  | Dueling DQN | Off |  |  | |
|  | [PER_DQN](./algos/PER_DQN/) | Off | [PER_DQN Paper](https://arxiv.org/pdf/1511.05952) | [wangzhongren](https://github.com/wangzhongren-code) |       |
|  | [NoisyDQN](./algos/NoisyDQN/) | Off | [NoisyDQN Paper](https://arxiv.org/pdf/1706.10295.pdf) | [wangzhongren](https://github.com/wangzhongren-code) |       |
|  | C51 | Off | [C51 Paper](https://arxiv.org/abs/1707.06887) | also called Categorical DQN | |
|  | Rainbow DQN |  |  |  | |
|  | QRDQN |  | [QRDQN Paper](https://arxiv.org/pdf/1710.10044.pdf) |  | |
|  | CQL |  | [CQL Paper](https://arxiv.org/pdf/2006.04779.pdf) |  | |
| Policy-based | [REINFORCE](./algos/REINFORCE/) | On | [REINFORCE Paper](http://www.cs.toronto.edu/~tingwuwang/REINFORCE.pdf) | [johnjim0816](https://github.com/johnjim0816) | 最基础的PG算法 |
|  | [A2C](./algos/A2C/) | On | [A2C blog](https://towardsdatascience.com/understanding-actor-critic-methods-931b97b6df3f) | [johnjim0816](https://github.com/johnjim0816) |       |
|  | [A3C](./algos/A3C/) | On | [A3C paper](https://arxiv.org/pdf/1602.01783) | [johnjim0816](https://github.com/johnjim0816), [Ariel Chen](https://github.com/cr-bh) |  |
|  | GAE |  |  |  |  |
|  | ACER |  |  |  |  |
|  | TRPO |  | [TRPO Paper](https://arxiv.org/abs/1502.05477) |  |  |
|                 |        [PPO](./algos/PPO/)         |       On      |                          [PPO Paper](https://arxiv.org/abs/1707.06347)                           |    [johnjim0816](https://github.com/johnjim0816), [Wen Qiu](https://github.com/clorisqiu1)     |  PPO-clip, PPO-kl     |
|  | [DDPG](./algos/DDPG/) | Off | [DDPG Paper](https://arxiv.org/abs/1509.02971) | [johnjim0816](https://github.com/johnjim0816) |       |
|  | [TD3](./algos/TD3/) | Off | [TD3 Paper](https://arxiv.org/pdf/1802.09477) | [johnjim0816](https://github.com/johnjim0816) |       |
| Multi-Agent | IQL                                |        | [IQL Paper](https://web.media.mit.edu/~cynthiab/Readings/tan-MAS-reinfLearn.pdf) |                                                              |       |
|  | VDN                                |        | [VDN Paper](https://arxiv.org/abs/1706.05296)                |                                                              | |
|  | QTRAN                              |        |                                                              |                                                              | |
|  | QMIX                               |        | [QMIX Paper](https://arxiv.org/abs/1803.11485)               |                                                              | |
|  | MAPPO                              |        |                                                              |                                                              | |
|  | MADDPG                             |        |                                                              |                                                              | |
| Sparse reward | Hierarchical DQN                   |        | [H-DQN Paper](https://arxiv.org/abs/1604.06057)              |                                                              | |
|  | ICM                                |        | [ICM Paper](https://arxiv.org/pdf/1705.05363.pdf)            |                                                              | |
|  | HER                                |        | [HER Paper](https://arxiv.org/pdf/1707.01495.pdf)            |                                                              | |
| MaxEntropy RL | [SoftQ](./algos/SoftQ/) | off | [SoftQ Paper](https://arxiv.org/abs/1702.08165) | [johnjim0816](https://github.com/johnjim0816) | |
|  | SAC |  |  |  | |
| Imitation Learning | [GAIL](./algos/GAIL/) |  | [GAIL Paper](https://arxiv.org/abs/1606.03476) | [Yi Zhang](https://github.com/ai4drug) | TODO |
|  | TD3+BC |  | [TD3+BC Paper](https://arxiv.org/pdf/2106.06860.pdf) |  |  |
| Model based | Dyna Q |  | [Dyna Q Paper](https://arxiv.org/abs/1801.06176) |  |  |