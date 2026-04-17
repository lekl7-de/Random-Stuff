### /HandBrake/CheatSheet

# SVT-AV1 Cheat Sheet

###  These arguments are included in my preset. 

```bash
film-grain-denoise=0
film-grain=8
enable-qm=1
qm-min=0
qm-max=15
enable-variance-boost=1
enable-overlays=0
enable-dg=1
irefresh-type=2
lookahead=120
keyint=10s
sparpness=2
enable-cdef=1
enable-restoration=1
enable-dlf=1
enable-tf=0
```


These settings are tuned for:

* **High visual quality**
* **Film grain preservation**
* **Advanced AV1 features**
* **Efficient compression**




## Film Grain & Noise

### `film-grain-denoise=0`

* Disables denoising before grain synthesis
* Keeps original noise intact




### `film-grain=8`

* Adds synthetic film grain (range: ~0–50+)
* `8` = moderate, natural-looking grain

**Effect:**

* Improves compression by replacing real noise with synthetic grain



## Quantization & Matrices

### `enable-qm=1`

* Enables **Quantization Matrices (QM)**
* Better detail distribution across frequencies


### `qm-min=0` / `qm-max=15`

* Controls QM strength range

| Value | Effect            |
| ----- | ----------------- |
| 0     | minimal influence |
| 15    | maximum influence |



## Detail Enhancement

### `enable-variance-boost=1`

* Boosts detail in high-variance areas

**Effect:**

* Sharper textures
* Slightly higher bitrate usage


## Overlay & GOP

### `enable-overlays=0`

* Disables overlay frames


### `enable-dg=1` (Dynamic GOP)

* Enables dynamic GOP structure

**Effect:**

* Better bitrate allocation
* More efficient scene handling


## Keyframes & Refresh

### `irefresh-type=2`

* Uses rolling intra refresh instead of classic keyframes

| Value | Meaning               |
| ----- | --------------------- |
| 0     | standard keyframes    |
| 1 / 2 | rolling intra refresh |


### `keyint=10s`

* Keyframe interval: every 10 seconds

* -> Longer interval = better compression


## Lookahead

### `lookahead=120`

* Encoder analyzes 120 frames ahead

**Effect:**

* Improved decision-making
* Better quality
* Higher CPU & memory usage


## Sharpness

### `sparpness=2` *(likely typo → `sharpness`)*

* Controls deblocking sharpness

| Value | Effect                  |
| ----- | ----------------------- |
| 0     | softer image            |
| 2     | slightly sharper        |
| high  | may introduce artifacts |


## Post-Processing Filters

### `enable-cdef=1`

* Constrained Directional Enhancement Filter

* -> Reduces block artifacts


### `enable-restoration=1`

* Loop Restoration (Wiener + Self-Guided filters)

* -> Smart smoothing while preserving detail


### `enable-dlf=1`

* Deblocking Filter

* -> Removes block edges


### `enable-tf=0`

* Disables temporal filtering

Helps with:

* Grain preservation
* Avoiding "waxy" look