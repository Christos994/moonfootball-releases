# Moon Football — releases

The version manifest the game checks on launch. Public on purpose: the game
repository is private, and `raw.githubusercontent.com` serves nothing from a
private repo without a token — which an installed app cannot keep secret.

Nothing here is source. It is one file answering one question.

## Announcing a release

Edit [`version.json`](version.json) in the browser. No build, no deploy.

```json
{
  "latestVersion": "0.2",
  "storeUrl": "https://play.google.com/store/apps/details?id=com.christosgeorgoulakis.moonfootball",
  "releaseNotes": "Faster kick-offs and a fix for the league fanfare."
}
```

| Field | Meaning |
|---|---|
| `latestVersion` | The version now available. Must match **Player Settings → Version** of the build you published. |
| `storeUrl` | Where the UPDATE button sends people. Change it here when the game reaches Google Play — no rebuild needed. |
| `releaseNotes` | Optional. A sentence or two; the panel shrinks when it is empty. |

## Order of operations

Publish the build **first**, then edit this file. Announcing a version nobody
can download yet sends players to a store page that does not have it.

## Notes

- The prompt appears only when `latestVersion` is **newer** than the installed
  build, compared component by component as numbers — so `0.10` is correctly
  newer than `0.9`.
- Raw GitHub content is CDN-cached for about five minutes. Allow a few minutes
  between the edit and seeing it on a device.
- A player who taps LATER is not asked about that version again. The next one
  asks afresh.
