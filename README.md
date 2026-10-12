# mc-queue-coordinator

Admission-control design for overloaded Velocity networks. Queueing protects backend capacity; it cannot manufacture capacity, so every queue needs a bound, expiry, and clear overload response.

## Invariants
- One active ticket per authenticated UUID.
- Queue position is derived from server-owned ordering, never client input.
- Tickets expire and reconnects are idempotent within a short grace period.
- Backend health and capacity gate dispatch; dispatch is rate-limited.
- Redis is coordination, not the sole durable record of purchases or entitlements.

Set maximum wait and queue length from measured login drain rates. Monitor queue age percentiles and rejected admissions. MIT licensed.
