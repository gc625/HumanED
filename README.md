# HumanED



![alt text](https://github.com/gc625/HumanED/blob/master/diagram.png?raw=true)

`Controller.set_position` and `Controller.make_position` have
arguments which exactly mirror the fields documented in
`docs/reference.md`.  Omitting them (or specifying None), results in
them being omitted from the resulting register based command.

* position
* velocity
* feedforward_torque
* kp_scale
* maximum_torque
* stop_position
* watchdog_timeout

Finally, the `query` argument controls whether information is queried
from the controller or not.

## Controlling resolution ##

The resolution of commands, and of returned query data, is controlled
by optional constructor arguments to `Controller`.  By default, the
commands are all F32, and the query requests a subset of fields as
INT16.  Here is an example of setting those.

```
pr = moteus.PositionResolution()
pr.position = moteus.INT16
pr.velocity = moteus.INT16
pr.kp_scale = moteus.F32
pr.kd_scale = moteus.F32

qr = moteus.QueryResolution()
qr.mode = mp.INT8
qr.position = mp.F32
qr.velocity = mp.F32
qr.torque = mp.F32

c = moteus.Controller(position_resolution=pr, query_resolution=qr)
```
