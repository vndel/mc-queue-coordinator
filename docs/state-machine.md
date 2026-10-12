# Ticket state machine

`WAITING -> DISPATCHED -> CONNECTED`

`WAITING -> EXPIRED | CANCELLED`

- Assign an idempotency key at admission.
- Atomically transition a ticket before dispatch to prevent duplicate handoff.
- If backend handoff fails, return to WAITING only when the ticket remains valid.
- Do not expose internal queue keys or other players' identity data.
