# On Data-Driven Discovery Of Symbolic Differential Equations From Unsuitable Coordinates Using SINDy-Autoencoders

<div align="center">
    
<img width=800 src="https://github.com/psaegert/sindy-autoencoders-thesis/assets/36567814/ca177943-7b8d-46c9-b5da-0c84a5a73924"/>

<p>
(from '<a href="https://arxiv.org/abs/1904.02107">Data-driven discovery of coordinates and governing equations</a>' by K. Champion et al., edited)
</p>
</div>

## Abstract

"Machine Learning Methods have evolved to a powerful tool in many fields of science, including physics. While methods have become fast and sophisticated enough to learn a wide variety of tasks, they often come at the cost of interpretability. This problem can be partially overcome by making use of symbolic regression as shown in <a href="https://www.pnas.org/doi/full/10.1073/pnas.1517384113">[1]</a> and <a href="https://proceedings.neurips.cc/paper/2020/file/c9f2f917078bd2db12f23c3b413d9cba-Paper.pdf">[2]</a>, but it requires data in suitable coordinates. In my work, I assess and improve the SINDY-Autoencoder proposed by K. Champion et al. <a href="https://arxiv.org/abs/1904.02107">[3]</a>, which is designed to learn not only symbolic equations of motion from high-dimensional data, but also the coordinates in which the equations would be most conveniently formulated. I conduct a verification and replication of the proposed method before creating and evaluating variants which eventually lead to better and more reliable results."

## Results

### Non-Linear Pendulum

| SR-Method | Variant | Source | FVU_x [10^-4] ↓ | FVU_ddx [10^-4] ↓ | FVU_ddz [10^-2] ↓ |
| --------- | ------- | ------ | --------------- | --------------- | --------------- |
| SINDy | N/A | K. Champ. et al. <a href="https://arxiv.org/abs/1904.02107">[3]</a> | (8) | (3) | (2) |
| SINDy | O1 | Output <a href="https://github.com/kpchamp/SindyAutoencoders">[13]</a> | (3) | (4) | (2.1) |
| SINDy | O1 | Verified | 1.1 | 2.0 | 0.4 |
| SINDy | O2 | Output <a href="https://github.com/kpchamp/SindyAutoencoders">[13]</a> | (9) | (10) | (21) |
| SINDy | O2 | Verified | 3 | 8 | 13 |
| SINDy | V {1-10} | Verified | **7±6** | 27±22 | 30±40 |
| SINDy | R {1-10} | Replicated | **7±6** | 26±21 | 50±40 |
| SINDy | PTAT {1-10} | Modified | 9±13 | **8±6** | **2.1±0.9** |
| pySR | pAE {1-10} | Modified | 500±260 | 16k±14k | 40±80 |

### Chaotic Lorenz System

**In-Distribution**
| SR-Method | Variant | Source | FVU_x [10^-5] ↓ | FVU_dx [10^-4] ↓ | FVU_dz [10^-4] ↓ |
| --------- | ------- | ------ | --------------- | --------------- | --------------- |
| SINDy | O1 | K. Champ. et al. <a href="https://arxiv.org/abs/1904.02107">[3]</a> | (3) | (2) | (7) |
| SINDy | O1 | Output <a href="https://github.com/kpchamp/SindyAutoencoders">[13]</a> | (2.7) | (5) | (7) |
| SINDy | O1 | Verified | 2.7 | 1.8 | 10 |
| SINDy | O2 | K. Champ. et al. <a href="https://arxiv.org/abs/1904.02107">[3]</a> | (0.2) | (0.6) | (3) |
| SINDy | O2 | Output <a href="https://github.com/kpchamp/SindyAutoencoders">[13]</a> | (0.2) | (0.9) | (5) |
| SINDy | O2 | Verified | 0.2 | 1.1 | 6 |
| SINDy | V {1-10} | Verified | 5±4 | 11±8 | 45±20 |
| SINDy | R {1-10} | Replicated | 5±4 | 10±6 | 39±15 |
| SINDy | PTAT {1-10} | Modified | **2.7±1.5** | **7.2±2.0** | **36±9** |
| pySR | pAE {1-10} | Modified | 3±3 | 5.0k±1.9k | 4.0k±1.4k |

**Out-Of-Distribution**
| SR-Method | Variant | Source | FVU_x [10^-2] ↓ | FVU_dx [10^-2] ↓ | FVU_dz [10^-2] ↓ |
| --------- | ------- | ------ | --------------- | --------------- | --------------- |
| SINDy | O1 | K. Champ. et al. <a href="https://arxiv.org/abs/1904.02107">[3]</a> | - | - | - |
| SINDy | O1 | Output <a href="https://github.com/kpchamp/SindyAutoencoders">[13]</a> | (1.3) | (11) | (8) |
| SINDy | O1 | Verified | 1 | 9 | 8 |
| SINDy | O2 | K. Champ. et al. <a href="https://arxiv.org/abs/1904.02107">[3]</a> | - | - | - |
| SINDy | O2 | Output <a href="https://github.com/kpchamp/SindyAutoencoders">[13]</a> | (1.5) | (10) | (6) |
| SINDy | O2 | Verified | 2.1 | 14 | 8 |
| SINDy | V {1-10} | Verified | **1.6±0.4** | 16±3 | 24±5 |
| SINDy | R {1-10} | Replicated | 1.6±0.5 | **13.1±2.5** | **18±5** |
| SINDy | PTAT {1-10} | Modified | 1.9±0.7 | 15±5 | 22±6 |
| pySR | pAE {1-10} | Modified | 510±120 | 6.7k±2.1k | 9k±3k |

### Reaction-Diffusion System
| SR-Method | Variant | Source | FVU_x [10^-2] ↓ | FVU_dx [10^-2] ↓ | FVU_dz [10^-2] ↓ |
| --------- | ------- | ------ | --------------- | --------------- | --------------- |
| SINDy | O1 | K. Champ. et al. <a href="https://arxiv.org/abs/1904.02107">[3]</a> | (1.6) | (1.6) | (0.2) |
| SINDy | O1 | Output <a href="https://github.com/kpchamp/SindyAutoencoders">[13]</a> | (1.6) | (1.6) | (0.2) |
| SINDy | O1 | Verified | 1.6 | 1.6 | 0.21 |
| SINDy | O2 | K. Champ. et al. <a href="https://arxiv.org/abs/1904.02107">[3]</a> | - | - | - |
| SINDy | O2 | Output <a href="https://github.com/kpchamp/SindyAutoencoders">[13]</a> | (1.6) | (1.6) | (0.8) |
| SINDy | O2 | Verified | 1.6 | 1.6 | 0.8 |
| SINDy | V {1-10} | Verified | 1.69±0.24 | 2.1±1.2 | 14±29 |
| SINDy | R {1-10} | Replicated | 1.64±0.1 | 1.9±0.6 | 14±22 |
| SINDy | PTAT {1-10} | Modified | 0.16±0.05 | **0.18±0.04** | **0.103±0.023** |
| pySR | pAE {1-10} | Modified | **0.067±0.010** | 0.28±0.12 | 0.26±0.12 |


## Code
https://gitlab.com/psaegert/sindy-autoencoders-improvements

## Citation
```bibtex
@misc{sindy-ae-improvements-saegert-22,
    author = {Paul Saegert},
    title = {On Data-Driven Discovery Of Symbolic Differential Equations From Unsuitable Coordinates Using SINDy-Autoencoders},
    month = may,
    year = 2022,
    publisher = {GitHub},
    school = "Heidelberg University",
    url = {https://github.com/psaegert/sindy-autoencoders-thesis}
}
```
