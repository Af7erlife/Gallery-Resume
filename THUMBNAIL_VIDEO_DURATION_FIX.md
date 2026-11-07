# Thumbnail video duration fix

The Android MediaStore `DURATION` column is measured in milliseconds and may exceed the range of a 32-bit integer for longer videos. The previous implementation read it through `getIntValue`, which could overflow before converting to seconds.

The media fetcher now reads `DURATION` as a `Long`, converts milliseconds to seconds, and safely clamps the result to the `Int` range used by `Medium.videoDuration`. The thumbnail adapter continues formatting that seconds value using the existing duration formatter.
