# Decision Tree


AI Tree

```
Enemy in Range?
├── No
│   ├── Move Toward Enemy
│   └── Take Cover
└── Yes
    ├── Low Health?
    │   ├── Yes → Retreat or Use Healing Item
    │   └── No
    │       ├── Flanked?
    │       │   ├── Yes → Reposition
    │       │   └── No → Attack Most Threatening Enemy
    └── Special Ability Ready?
        ├── Yes → Use Ability on High Value Target
        └── No → Continue Standard Attack
```

determining whether an enemy is “in range” depends on how the game or simulation defines:
	•	Range mechanics (e.g., weapon distance, vision radius)
	•	Entity positioning (e.g., grid, 3D coordinates)

### Pseudocode: IsEnemyInRange

```
FUNCTION IsEnemyInRange(selfPosition, enemyPosition, rangeRadius)
    distance = CalculateDistance(selfPosition, enemyPosition)
    RETURN distance <= rangeRadius
END FUNCTION

FUNCTION CalculateDistance(a, b)
    RETURN SquareRoot((a.x - b.x)^2 + (a.y - b.y)^2 + (a.z - b.z)^2)
END FUNCTION
```

