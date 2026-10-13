# TideMusic 🎧

A mobile-first Spotify-connected music player, built as a zero-build static website.

## Features

- Spotify login with Authorization Code + PKCE (no client secret in the browser)
- Browser playback with the Spotify Web Playback SDK
- Search tracks, open tracks in Spotify, save/remove liked tracks
- Liked Songs and your Spotify playlists
- Playlist playback where your Spotify account has API access
- Queue, previous/next, play/pause, seek, volume and device selection
- Mobile layout, keyboard-accessible controls and in-app connection diagnostics

## Before Spotify login works

1. The app's Spotify developer account **must have Premium**. Users need Spotify Premium for Web Playback SDK playback.
2. Visit the [Spotify developer dashboard](https://developer.spotify.com/dashboard), open the existing Spotify app, and add the exact production URL **`https://tidemusic-test.vercel.app/`** to **Redirect URIs**, if it is not already there. Save.
3. For local development on your own computer, use a configured loopback redirect. Spotify requires the redirect to match exactly, including the slash; the app always uses the current page URL.
4. Spotify's development mode restricts sign-in to explicitly allowed users. Add the tester in the app's **User Management** area when applicable. Limits depend on the app's creation date and Spotify's rules.
5. Use an HTTPS origin or an accepted localhost origin. Enable DRM / protected content in your browser if the SDK cannot play.

If login shows `INVALID_CLIENT`, check the Spotify Redirect URI and that the app's client ID is valid. If playback fails, tap **ⓘ** inside TideMusic to see the playback and API errors. Browsers may require another physical tap on Play to allow audio.

## Hosting

The site is just `index.html` and `vercel.json`; no framework, build command or environment secrets are required. The intended existing Vercel project is **`tidemusic-test`** (production URL: `https://tidemusic-test.vercel.app/`).

**Note:** As of this update, the Vercel project is not connected to this repository's Git integration. To enable automatic publishing, connect `jdarkyeka6/TideMusic` to the existing `tidemusic-test` Vercel project and set the production branch to `main`, or import the repository as a separate project. The current project may have Vercel Authentication protection enabled, which affects public access.

## Notes

- All Spotify audio streams through Spotify. There is no music hosting or downloading.
- Tokens are held in browser `sessionStorage`, rather than in source or URL fragments. Signing out removes app tokens.
- Song availability and playback permissions depend on the Spotify account and API restrictions.
- The 2026 Spotify playlist API restricts item access for playlists not owned by the user or shared with the user as a collaborator.
- Licensed Spotify content and metadata remain subject to Spotify's platform terms.

