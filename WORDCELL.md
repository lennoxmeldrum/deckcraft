# WordCell patches

This fork's `wordcell` branch is [storytold/deckcraft](https://github.com/storytold/deckcraft)
`main` plus the small "host mode" changes [WordCell](https://github.com/lennoxmeldrum/wordcell)
needs to show DeckCraft as one of its tabs. `main` mirrors upstream unchanged. Each change is its
own commit and is meant to be offered upstream; when upstream has it, drop it here.

| # | Change | Commit subject | Upstream PR |
|---|---|---|---|
| D1 | `SlideApp::reinstall_context`: install DeckCraft's fonts and theme again | WordCell host: SlideApp::reinstall_context | not yet opened |
| D2 | `Session::document_mut(uid)`: a host marks any open presentation saved | WordCell host: Session::document_mut by uid | not yet opened |

DeckCraft needs nothing else to be hosted: the rest of its `Session` API is public, `integrated_titlebar`
already leaves the macOS window buttons to the host, and `SlideApp` draws one window (plus
Presenter View and View › New Window, which open windows of their own).

Upstream's own workflows are disabled in this fork (Actions › each workflow › Disable): they need
storytold's secrets and shared actions. Only `sync-upstream.yml` runs: daily, it mirrors upstream
`main` and merges it into `wordcell` (or opens an issue if WordCell's patches conflict). It needs a
`WORDCELL_BOT_TOKEN` secret; see that file's header.
