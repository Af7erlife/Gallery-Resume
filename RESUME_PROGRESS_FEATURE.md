# Folder resume progress modification

This fork adds per-folder resume of the last viewed media item.

## Behavior
- When media is opened from a folder inside Fossify Gallery, the last viewed media path is saved for that folder.
- The next time that folder is opened in the viewer, the viewer selects the saved media item instead of the item initially tapped.
- Each folder has an independent saved path.
- Favorites, Recycle Bin, and external `VIEW` intents are excluded.
- If the saved file was removed or is no longer in the folder's media list, the viewer falls back to the newly selected item.

## Video playback timestamp
Fossify Gallery already implements per-video playback-position persistence. Enable **Settings → Video → Remember last video position** (wording may vary by app version) to resume the video at its previous playback timestamp as well as restoring that video as the folder's last viewed item.

## Implementation
`ViewPagerActivity` stores `last_media_path:<folder path>` in private SharedPreferences and restores it when the folder's media list is loaded. The existing `VideoFragment` playback-position implementation is retained.
