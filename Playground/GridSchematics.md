# Grid Schematics

Here are instructions on how to create a grid.

## Divide up grid cells.

```
gridX = floor(worldX / cellSize)
gridY = floor(worldY / cellSize)
```

## Cell Data Structure

```
Grid[row][col] = Cell {
    occupied: bool
    terrainType: "grass" | "water" | "mountain"
    movementCost: number
    entity: reference or null
}
```

### Customize Terrain
```
grid[3][5].terrainType = "water"
grid[3][5].movementCost = 1000        // water is impassable
```

```
grid[1][1].terrainType = "road"
grid[1][1].movementCost = 0.5         // fast movement
```

### Create Grid Container

```
FUNCTION CreateGrid(rows, cols)
    grid = []

    FOR y FROM 0 TO rows - 1 DO
        row = []
        FOR x FROM 0 TO cols - 1 DO
            cell = {
                occupied: false,
                terrainType: "grass",       // default
                movementCost: 1,            // base cost
                entity: null
            }
            row.Append(cell)
        END FOR
        grid.Append(row)
    END FOR

    RETURN grid
END FUNCTION
```

### Placing Entities on the Grid

```
FUNCTION PlaceEntity(grid, x, y, entity)
    IF grid[y][x].occupied == false THEN
        grid[y][x].entity = entity
        grid[y][x].occupied = true
    END IF
END FUNCTION
```

## Construction Algorithm

```
Initialize Grid
├── Get World Dimensions from Framework
│   └── Define rows and columns based on cell size
├── For Each Tile or Object in World
│   └── Map to Grid Cell using position / cell size
├── Store Data in Grid
│   ├── Is Occupied?
│   ├── Terrain Type?
│   └── Movement Cost
└── (Optional) Add Navigation Tags or AI Flags
```

# Grid System Example

This document describes a grid-based system for representing tactical or simulation environments. Each cell holds key data about terrain, occupancy, movement cost, and entities.

---

## Grid Cell Structure

```plaintext
Grid[row][col] = Cell {
    occupied: bool
    terrainType: "grass" | "water" | "mountain"
    movementCost: number
    entity: reference or null
}
```

```
G = Grass (movement cost: 1)
W = Water (movement cost: ∞ or impassable)
M = Mountain (movement cost: 3)
O = Occupied
. = Empty
E = Entity present

+----+----+----+----+----+
| G. | G. | W. | M. | G. |
+----+----+----+----+----+
| G. | E. | G. | M. | G. |
+----+----+----+----+----+
| G. | G. | G. | G. | G. |
+----+----+----+----+----+
| M. | G. | G. | G. | G. |
+----+----+----+----+----+
| W. | G. | G. | E. | 

```

# Grid [1][1]
```json
{
  "occupied": true,
  "terrainType": "grass",
  "movementCost": 1,
  "entity": "Knight"
}

```
# Grid [0][2]
```json
{
  "occupied": false,
  "terrainType": "water",
  "movementCost": 9999,
  "entity": null
}

```
# Grid [4][3]
```json
{
  "occupied": true,
  "terrainType": "grass",
  "movementCost": 1,
  "entity": "Goblin"
}
```
