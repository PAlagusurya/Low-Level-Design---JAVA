# Entity Design

## User

```
User
- id: Long
- phone: String
- email: String
- password: String
```

## Event

```
Event
- id: Long
- eventName: String
- startDate: LocalDate
- endDate: LocalDate
- submissionDueDate: LocalDate
- winningItem: String
- eventStatus: Enum (ACTIVE / FINISHED)
- eventResult: Enum (PROCESSING / DECLARED)
- winningBid: Integer
```

## Set

```
Set
- id: Long
- user: User         → Many Sets to One User
- event: Event       → Many Sets to One Event
- setNo: Integer
- status: Enum (PURCHASED / SUBMITTED)
- bids: List<Bid>
```

## Bid

```
Bid
- id: Long
- bidNumber: Integer
- set: Set           → Many Bids to One Set
```

---

## Relationships

| Relationship | Type         |
| ------------ | ------------ |
| User ↔ Event | Many to Many |
| Set → User   | Many to One  |
| Set → Event  | Many to One  |
| Bid → Set    | Many to One  |

> **Note:** The `Set` entity acts as the junction table between User and Event, naturally resolving the Many to Many relationship.
