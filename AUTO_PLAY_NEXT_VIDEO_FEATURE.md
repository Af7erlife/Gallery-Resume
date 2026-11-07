# Automatic next-video playback

This revision adds an independent `Automatically play next video` setting. When a video reaches the end in the folder viewer, the app searches forward in the current folder's active sort order, skips non-video media, and opens the next video. The destination VideoFragment is explicitly instructed to start playback as soon as its player is prepared, avoiding the intermediate paused/unplayed state.

`Loop videos` and `Automatically play next video` are mutually exclusive in Settings. If no later video exists, playback remains stopped at the end. Existing folder resume-by-path behavior is retained.
