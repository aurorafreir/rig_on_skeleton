# rig_on_skeleton

Hi! This is a set of tools for programmatically creating rigs on top of pre-built skeletons

This toolset is currently designed to be run entirely through code, with the 

The main functional code is situated in `rig_on_skeleton.py`, and there are two example scripts for the rig building. 
These are `metahuman.py` and `brooke.py`.

## How to run
```python
from rig_on_skeleton import metahuman  # Replace this with the specific runner module
from importlib import reload  # Reloads only need to be added if you're actively working on the code
reload(metahuman)
metahuman.run()
```

## Supported functionality:

- ### Class based Main Rig and Limb system (`$Rig` and `$Limb`)
- ### Class based controller creation (`$CtrlSet`)
- ### Class based attribute creation (`$Attr`)
- ### Automatic pole vector placement
- ### Locking and Hiding of non-animation friendly attributes

- ### (In Progress) Three Bone Limb (Arms/Legs) (`$ThreeBoneLimb`)::
  - ![#c5f015](https://placehold.co/15x15/c5f015/c5f015.png) (Working) FKIK
  - ![#c5f015](https://placehold.co/15x15/c5f015/c5f015.png) (Working) Pole Locking
  - ![#D9743B](https://placehold.co/15x15/D9743B/D9743B.png) (In Progress) Limb Stretch
  - ![#1589F0](https://placehold.co/15x15/1589F0/1589F0.png) (Planned) Arbitrary twist bones
  - ![#1589F0](https://placehold.co/15x15/1589F0/1589F0.png) (Planned) Control Space Switching

- ### (Planned) Digitigrade Leg (4 bone leg, e.g. Dog legs)