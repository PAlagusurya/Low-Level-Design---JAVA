# API Design

## Authorization Model

| API               | Auth Type          |
| ----------------- | ------------------ |
| Create Event      | systemToken        |
| Declare Winner    | systemToken        |
| Buy a Set         | accessToken (user) |
| Submit Bids       | accessToken (user) |
| Get Active Events | None (public)      |
| See Past Winners  | None (public)      |

---

## 1. Create Event (System)

```
POST /events
headers: { Authorization: systemToken }
request: { eventName, startDate, endDate, winningItem }
response: { eventId, eventName, startDate, endDate, submissionDueDate, status: "ACTIVE" }
```

## 2. Get Active Events (Public)

```
GET /events
request: {}
response: [{ eventId, eventName, winningItem, endDate, status }]
```

## 3. Buy a Set (User)

```
POST /events/sets
headers: { Authorization: accessToken }
request: { eventId, setNumber: 1 }
response: { setId, setNumber, coinsDeducted, remainingCoins, status: "PURCHASED" }
```

## 4. Submit Bids (User)

```
POST /events/sets/{setId}/bids
headers: { Authorization: accessToken }
request: { bids: [2, 3, 4, 5, 6, 8] }
response: { setId, bids, status: "SUBMITTED" }
```

## 5. Declare Winner (System)

```
PATCH /events/{eventId}/winner
headers: { Authorization: systemToken }
request: {}
response: { status: "WINNER_DECLARED", eventId, winnerId, winningBid }
```

## 6. See Past Winners (Public)

```
GET /events/winners?page=1&limit=10
request: {}
response: {
  total, page,
  data: [{ eventId, winnerId, winningItem, winningBid, eventDate }]
}
```
