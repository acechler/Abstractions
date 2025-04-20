# Entity Logic

## pathfinding
FUNCTION MoveEntity3D(Position, Direction, Speed, DeltaTime, Constraints)
    // Normalize the direction vector
    Direction = Normalize(Direction)

    // Compute velocity
    Velocity = Direction * Speed * DeltaTime

    // Calculate new position
    NewPosition.x = Position.x + Velocity.x
    NewPosition.y = Position.y + Velocity.y
    NewPosition.z = Position.z + Velocity.z

    // Apply constraints, such as bounds or collisions
    IF Constraints ARE DEFINED THEN
        NewPosition = ApplyConstraints(NewPosition, Constraints)
    END IF

    // Update entity position
    Position = NewPosition

    RETURN Position
END FUNCTION


FUNCTION Normalize(Vector)
    Magnitude = SquareRoot(Vector.x^2 + Vector.y^2 + Vector.z^2)
    IF Magnitude == 0 THEN
        RETURN (0, 0, 0)
    END IF
    RETURN (Vector.x / Magnitude, Vector.y / Magnitude, Vector.z / Magnitude)
END FUNCTION


FUNCTION ApplyConstraints(Position, Constraints)
    // Example: Clamp within world bounds
    Position.x = Clamp(Position.x, Constraints.MinX, Constraints.MaxX)
    Position.y = Clamp(Position.y, Constraints.MinY, Constraints.MaxY)
    Position.z = Clamp(Position.z, Constraints.MinZ, Constraints.MaxZ)

    // Optionally, check for collisions, gravity, etc.

    RETURN Position
END FUNCTION