## Usage

### Map generation

To generate a map, run from pps-election folder root:

```bash
python3.7 -m election.g6.srcipts.generatemap
```

If you want to modify the default parameters:

```bash
python3.7 -m election.g6.srcipts.generatemap \\
    -m election.g6.src.mapgenerator \\
    -o maps/g6/1.map \\
    --seed 42 \\
    --voters 333333 \\
    --parties 3
```

### District generation


To generate districts, you have to go through three steps:
1. Triangulation
2. Triangles to graph
3. District generation

#### Triangulation

#### Triangles to graph

Run:
```
python3 -m election.g6.srcipts.text_triangles_to_pickle
```

Parameters:
```bash
usage: text_triangles_to_pickle.py [-h] [--input INPUT]
                                   [--input-map INPUT_MAP] [--output OUTPUT]

optional arguments:
  -h, --help            show this help message and exit
  --input INPUT, -i INPUT
                        Path to triangles from physical simulation
  --input-map INPUT_MAP, -im INPUT_MAP
                        Path to input map for which the triangles where
                        generated
  --output OUTPUT, -o OUTPUT
                        Path to where to save the pickle with graph and
                        triangles

```

#### District generation

Run from pps-election folder root:

```bash
python3.7 -m election.g6.srcipts.generatedistricts -i maps/g7/3.map
```

If you want to modify the default parameters:

```bash
usage: generatedistricts.py [-h] [--module MODULE] [--input INPUT]
                            [--input-map INPUT_MAP] [--n-iters N_ITERS]
                            [--gerrymander-for GERRYMANDER_FOR]
                            [--output OUTPUT] [--seed SEED]
                            [--representatives REPRESENTATIVES]

optional arguments:
  -h, --help            show this help message and exit
  --module MODULE, -m MODULE
                        Python module to use as district generator
  --input INPUT, -i INPUT
                        Path to pickle with graph and triangles
  --input-map INPUT_MAP, -im INPUT_MAP
                        Path to map file to gerrymander
  --n-iters N_ITERS     Number of iteration to run gerrymandering for
  --gerrymander-for GERRYMANDER_FOR
                        Party index for which to gerrymander [0, 1, 2]
  --output OUTPUT, -o OUTPUT
                        A path where to save the final map
  --seed SEED           Random seed
  --representatives REPRESENTATIVES
                        Number of representatives per district [1, 3]

```