# Vynic technical distribution origin

This repository contains no public installer landing page or application source.
The release remains draft: every binary asset requires private storage access.

Authenticated Admin/customer flows issue a temporary bearer link under
`https://releases.vynic.ge/windows/access/<non-secret-grant-id>#token=<secret>`.
The Render static site's only delivery mapping is `/windows/access/*` to
`https://api.vynic.ge/customer/downloads/access/*` (HTTP redirect). The fragment
never reaches Render/GitHub request URLs. Backend exchange scopes an HttpOnly
cookie to that grant; every artifact GET, HEAD and byte range rechecks it, expiry,
revocation, the active issuer, and customer ownership/POS entitlement. The public
selector alone cannot retrieve bytes. Links are bearer capabilities: forwarding
the complete link grants the recipient download access until it expires/revokes.

Root and unknown paths return neutral 404, with no installer list or signup page.
Build check: `test -f public/robots.txt`. Publish directory: `public`.
Automatic updates remain inactive pending separate device authorization and release
qualification. The offline installation package retains the signed POS/Edge
metadata and payload hashes. Do not publish its draft release or private keys.
