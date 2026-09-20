# Requirements

## Concepts

### What is a Bid?

A single number submitted to compete. For example, "23" is one bid.

### What is a Set?

A collection of 6 bids grouped together. Think of it like a lottery ticket — the ticket is the set, the numbers on it are the bids.

### Pricing per Set

| Set Number | Cost (CRED Coins) |
| ---------- | ----------------- |
| 1st Set    | 100 coins         |
| 2nd Set    | 500 coins         |
| 3rd Set    | 1000 coins        |
| 4th Set    | 1500 coins        |
| 5th Set    | 2000 coins        |

- Maximum **5 sets** per user per event
- Each set contains maximum **6 bids**
- Each event displays only **one winning item**

## System Can:

- Add a new event with a winning item
- Declare winner of a bidding event

## Members Can:

- Participate in an event for a particular item
- Buy a set of bids using CRED coins
- Submit a set
- See latest winners of past events

## Winner Declaration Rules

- Member who places the **lowest unique bid** wins
- **Edge case — No unique bid exists:**
  - Winner is the member who submitted the **earliest set** containing the lowest bid
  - Example: If 78 is the lowest bid and 3 members have it, the one who submitted their set earliest wins
