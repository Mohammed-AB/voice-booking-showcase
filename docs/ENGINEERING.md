# Voice Booking: engineering notes

Speech is ambiguous, and a booking is a state change. Voice Booking separates what was heard, what was interpreted and what the user actually confirmed.

## System path

~~~mermaid
flowchart LR
  Audio --> Transcript
  Transcript --> BookingProposal
  BookingProposal --> UserCorrection
  UserCorrection --> Confirmation
  Confirmation --> PersistedBooking
  PersistedBooking --> SpokenReply
~~~

This diagram describes the demonstrated system boundary, not a production deployment topology.

## Decisions and tradeoffs

### Show the interpretation before commitment

The interface exposes transcript and booking summary. A correction changes the proposed time before a confirmation creates the booking.

### Keep speech consistent with state

Dedicated speech synthesis reads the authoritative response. The recorded reply is independently transcribed to check that an unconfirmed hold is not spoken as a completed booking.

### Make the reference intelligible

A discovered spoken-reference mismatch led to explicit digit pronunciation, then a second transcription check against the stored booking reference.

## Review questions

- What evidence demonstrates **show the interpretation before commitment**, and what would fail without it?
- What evidence demonstrates **keep speech consistent with state**, and what would fail without it?
- What evidence demonstrates **make the reference intelligible**, and what would fail without it?

## Verification boundary

Recorded synthetic spoken request, time correction and explicit confirmation, with a matching persisted calendar entry. Independent transcription checks of the generated replies, including the final booking reference. Typed interaction remains available when microphone or live provider access is unavailable. 20 unit, 15 database and eight browser checks passed; both builds passed.

Fictional bookings only. Live microphone capture depends on browser permission and available allowance. Telephony, physical-device audio and a production LiveKit deployment are not established by this recording.
