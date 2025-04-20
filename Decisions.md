

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
