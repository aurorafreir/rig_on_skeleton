# rig_on_skeleton documentation

rig_on_skeleton is a library of Python functions in order to programmatically create character rigs on top of a 
    pre-built skeleton.

It is designed for Python 3.7, and tested in Maya 2023.

It relies on PyMel in your MayaPy python packages.

# Basic rig file setup
Each character rig that I've built has it's own python "runner" script

I'll be using the `brooke.py` as an example, so all object names will be based on that character.
```python
import pymel.core as pm
from rig_on_skeleton import rig_on_skeleton as ros
```

# Basic rig setup
The `ros.Rig()` class contains basic setup that is used on any rig created with this system
```python
# -- FIRST SETUP --
    rig = ros.Rig()                 # Instantiate the rig class
    rig.main_grp = "brooke"         # This is the name of the group to place the rig parts and controls
    rig.ensure_setup_is_correct()   # Creates basic groups for future use
```

# Limb and Controller setup

```python
# -- ROOT CONTROLS --
    root_limb = ros.Limb()                      # Instantiate the Limb class to hold the limb data
    root_limb.limb_name = "root"                # Gives a name for the Limb
    root_limb.rig_parent = rig.rig_setup_grp    # Sets the parent group for the root limb's rig data
    root_limb.ctl_parent = rig.ctls_grp         # Sets the parent group for the root limb's control data
    
    global_ctl = ros.CtrlSet(
        ctl_name="global",
        ctl_shape="square_with_point",
        shape_size=25,
        parent=rig.ctls_grp,
        colour=ros.white,
    )
    global_ctl.create_ctl()

    global_off_ctl = ros.CtrlSet(
        ctl_name="global_off",
        ctl_shape="square",
        shape_size=20,
        parent=global_ctl.ctl,
        colour=ros.white,
    )
    global_off_ctl.create_ctl()

    root_ctl = ros.CtrlSet(
        ctl_name="root",
        ctl_shape="box",
        shape_size=2,
        parent=rig.ctls_grp,
        offset=True,
        spaceswitch=True,
    )
    root_ctl.create_ctl()

    # add ctls to root_limb.ctl attribute, and append root_limb to rig.limbs
    root_limb.ctls.extend([global_ctl, global_off_ctl, root_ctl])
    rig.limbs.append(root_limb)
```