# Simulate Virtual Rooms Configuration
Generate large-scale simulated room configuration

Sound source localization as show in figure below:
![image](example.png)

# How to use

```python
import param_generator

room_param_generator = param_generator.ParameterGenerator(
    sample_num=100,
    seed=1234,
    config={
        'room': {
            'x': [3, 10],
            'y': [3, 8],
            'z': [2.5, 6]
        },
        'target': {
            'azimuth': [-180, 180],
            'elevation': [-30, 180]
        },
        'noise': {
            'number': 3,
            'azimuth': [-180, 180],
            'elevation': [-30, 180]
        },
    }
)

for config in room_param_generator:
    if config is None:
        continue

    for source_type, config in config.items():
        print("="*20, source_type, "="*20)
        if source_type == "noise_sources":
            for i in config:
                print("    ", i)
        else:
            print("    ", config)


```

# Acknowledge
1. I borrowed some code from [sim-rir-preparation](https://github.com/tomkocse/sim-rir-preparation/blob/master/prep_sim_rirs.sh).
2. We can generate room simulations parameter with [room-simulation](https://github.com/ebezzam/room-simulation) and [pyroomacoustics](https://github.com/LCAV/pyroomacoustics).

# Citations
[Generation of large-scale simulated utterances in virtual rooms to train deep-neural networks for far-field speech recognition in Google Home](https://static.googleusercontent.com/media/research.google.com/zh-CN//pubs/archive/46107.pdf)
