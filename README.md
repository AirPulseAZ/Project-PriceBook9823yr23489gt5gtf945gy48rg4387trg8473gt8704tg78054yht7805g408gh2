# AirPulse private price book

This is a separate static website from the AirPulse customer-facing business site. It has no backend and no external dependencies. Publish it in a separate repository. Upload this folder's contents (index.html at the root), then select Settings → Pages → Deploy from a branch → main → / (root). Use HTTPS. You can also open index.html locally in a modern browser.

The password is provided separately in AirPulse-Owner-Access.txt. NEVER upload that file. The source and login page are visible to visitors; the catalog is encrypted using AES-256-GCM, PBKDF2-SHA256 with 600,000 iterations, a random 128-bit salt and 96-bit IV. The random initial password is not in this website. Keep it private. No password is sent to a server. There is no password recovery.

## Pricing

The starting rate is 52% **markup on cost**, not gross margin. Selling price = (material / other cost + direct labor cost) × 1.52. A $100 total cost sells for $152, corresponding to 34.21% gross margin before overhead and taxes. If you intend 52% gross margin instead, the calculation would be cost / 0.48; that is not this app's formula.

The broad starter catalog includes capacitors, electrical controls, motors, thermostats, refrigerant, sealed-system parts, heating components, coils, drains, ductwork, filtration, services, system installation templates, and extras. It cannot cover every SKU, manufacturer, or labor scenario. Only a few previously supplied costs are populated. Verify them before quoting. Unknown costs are blank and do not produce selling prices. Add, edit, or delete items to suit your business. Direct labor costs are not your retail hourly labor rate. Part-only prices exclude installation.

## Keeping edits

Edits stay in memory until you choose **Save encrypted file**. This downloads an updated `vault.js`. Save it somewhere you control. To persist changes on the website, replace `vault.js` in its GitHub repository with the downloaded file. If your browser appends a suffix, rename it to `vault.js` before uploading. You can also load a downloaded copy at the unlock screen. Never paste plain costs into website source or upload the owner instructions.

The site cannot automatically write to GitHub and has no live supplier synchronization. Closing or refreshing without saving loses changes. No plaintext price book or password is stored in localStorage. Auto-lock after 10 minutes of inactivity re-encrypts current data in that tab; unlock and download it before closing. Keeping old encrypted backups also preserves their old passwords and data.

Changing the password creates a new encrypted download; replace the hosted `vault.js` to update the hosted copy. A password change does not revoke access to historical copies. Keep repository write access secure, as someone who can change website code can change its behavior.

The business website has no link to this site. Anyone with this site's URL can see the unlock screen; only someone with the vault password can decrypt the pricing. This is password encryption, not individual account authentication or a backend access-control service.

Official references:
- https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site
- https://developer.mozilla.org/en-US/docs/Web/API/SubtleCrypto/encrypt
- https://developer.mozilla.org/en-US/docs/Web/API/SubtleCrypto/deriveKey
