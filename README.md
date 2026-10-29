# SteelyGamma levels

Options-derived gamma levels for NQ futures (call wall, put wall, gamma flip), from SteelyLabs.

**Levels:** https://raw.githubusercontent.com/Steely-Systems/steelygamma-levels/main/latest.json

## When it updates
Each weekday, in two stages (the `stage` field):

| Stage | Time (ET) | Anchored to |
|---|---|---|
| `premarket` | about 08:30 | NQ at run time |
| `open` | about 09:50, replaces premarket | prices at 09:35 |

The walls are fixed for the day.

## Fields
- `nq.ndx` and `nq.qqq`: levels already mapped to the NQ contract named in `anchor.nq_contract`, from Nasdaq-100 index
  options and QQQ options. When the two sets agree, the level is stronger.
  - `call_wall`, `put_wall`: the strike above / below price with the most call / put gamma.
  - `call_wall_2`, `put_wall_2`: the runner-up strikes, which are often nearly tied.
  - `gamma_flip`: SteelyGamma's estimate of where net dealer gamma crosses zero. `null` if there's none within ±10%.
- `ndx`, `qqq`: the same levels in index and QQQ prices. `*_gex_bn` is dollar gamma per 1% move, in billions.
  `net_gex_bn` below 0 means dealers are short gamma.
- `oi_new`: `false` if that day's open interest wasn't available yet at run time.

Not trading advice.
