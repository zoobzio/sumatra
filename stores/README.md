# stores

Data access layer implementations.

## Purpose

Implement contracts using `sum.Database`, `sum.Store`, or `sum.Bucket` wrappers. Stores handle all database queries and storage operations.

## Pattern

```go
// stores/users.go
package stores

import (
    "context"

    "github.com/jmoiron/sqlx"
    "github.com/zoobzio/astql"
    "github.com/zoobzio/sum"
    "github.com/zoobzio/sumatra/models"
)

type Users struct {
    *sum.Database[models.User]
}

func NewUsers(db *sqlx.DB, renderer astql.Renderer) (*Users, error) {
    database, err := sum.NewDatabase[models.User](db, "users", renderer)
    if err != nil {
        return nil, err
    }
    return &Users{Database: database}, nil
}

// GetByLogin retrieves a user by their login name.
func (s *Users) GetByLogin(ctx context.Context, login string) (*models.User, error) {
    return s.Select().
        Where("login", "=", "login").
        Exec(ctx, map[string]any{"login": login})
}
```

## Aggregate Factory

```go
// stores/stores.go
package stores

import (
    "github.com/jmoiron/sqlx"
    "github.com/zoobzio/astql"
    "github.com/zoobzio/grub"
)

type Stores struct {
    Users        *Users
    Repositories *Repositories
    // ... all stores
}

func New(db *sqlx.DB, renderer astql.Renderer, bucket grub.BucketProvider) (*Stores, error) {
    users, err := NewUsers(db, renderer)
    if err != nil {
        return nil, err
    }
    // ... create all stores

    return &Stores{
        Users: users,
        // ...
    }, nil
}
```

## Guidelines

- One store per domain entity
- Embed `*sum.Database[Model]` for SQL stores
- Use `sum.NewStore[Model]` for key-value stores
- Use `sum.NewBucket[Model]` for object storage
- Create custom query methods for anything beyond basic CRUD
- Use the Soy query builder for type-safe queries
- Keep `stores.go` as the aggregate factory
- Register stores against contracts in main.go
