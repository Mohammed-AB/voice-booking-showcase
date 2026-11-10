# Voice Booking: verification record

Review date: **10 November 2026**.

## Current mode

A recorded real speech-to-text, booking and spoken-response journey over a fictional calendar. HTTP push-to-talk is supported; this is not a claim of a completed WebRTC call deployment.

## Observed checks

- Recorded spoken request, spoken time correction and explicit confirmation, with a matching persisted calendar entry.
- Independent transcription checks of the generated replies, including the final booking reference.
- Typed interaction remains available when microphone or live provider access is unavailable.
- 20 unit, 15 database and eight browser checks passed; both builds passed.

These are scoped development checks, not an external audit or a claim of production adoption. Test fixtures are fictional. The private implementation workspace retains detailed test logs and provider receipts; this package carries the presentation evidence only.

## Explicit limits

Fictional bookings only. Live microphone capture depends on browser permission and available allowance. Telephony, physical-device audio and a production LiveKit deployment are not established by this recording.

## Package integrity

[Media manifest](../media-manifest.json) records the included filenames, byte sizes and SHA-256 digests. It identifies the exact presentation assets; a hash does not by itself prove the assertions above.
