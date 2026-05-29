---
"flowershow": patch
---

Surface server-side error messages to the user.

`FlowershowClient` now throws `FlowershowError` instead of plain `Error` for both API failures and R2 upload failures. The catch blocks in `main.ts` and `PublishStatusModal.tsx` already check `instanceof FlowershowError` to decide between the actionable notice (`❌ Can't publish: <message>`) and the generic "Check console" fallback — they were always falling through because the wrong exception type was thrown. Users now see the actual reason (invalid token, site name collision, etc.) when publishing fails.
