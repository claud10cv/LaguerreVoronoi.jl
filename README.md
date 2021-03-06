# LaguerreVoronoi
Compute Laguerre-Voronoi diagrams in Julia

## Usage
```julia
S = 10 * rand(10, 2) # centers of 10 balls
R = rand(1 : 5, 10) # radii of 10 balls
tri_list, V = LaguerreVoronoi.power_triangulation(S, R)
voronoi_dict = LaguerreVoronoi.compute_voronoi_cells(S, V, tri_list)
```

## Output
- `V: Array{Array{Float64, 1}, 1}`
  - containing the vertices of the power triangulation
- `tri_list: Array{Any, 1}`
  - containing the triplets for each triangulation
- `voronoi_dict: Dict{Int64,Array{Any,1}}`
  - Each entry of the dictionary is an array containing the cell borders. Each cell of that array is a tuple `((i, j), (v, d), s, t)` representing a segment `v + d * k`, with `s <= k <= t`. The tuple `(i, j)` refers to the indices of the vertices in `V` that form that segment. `nothing` is used to indicate a point in the infinite or an infinite scalar, for rays. 
