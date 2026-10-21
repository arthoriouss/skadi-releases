# Creating the Tally form (for the owner)

The "I don't have an account" button on the report page opens a Tally form, with the technical info prefilled through hidden fields.

1. Create a form on <https://tally.so> (the free plan is enough). Title: "SKADI - Report a problem".
2. Declare **hidden fields** (Form settings > Hidden fields, or type `/hidden`). Names must match exactly, lowercase:
   `v`, `b`, `p`, `m`, `os`, `srv`, `cat`, `lang`
   (version, build, platform, device model, OS, servers, category, language).
3. Add the visible questions:
   - **What happened?** - long text, required.
   - **Steps to reproduce** - long text, optional.
   - **What did you expect?** - long text, optional.
   - **E-mail (optional, only if you want a reply)** - email input, optional. Help text: "Used only to follow up on this report. Leave empty to stay anonymous."
   - **Consent** - checkbox, required only if an e-mail is entered (conditional logic): "I agree that my e-mail address is used only to reply to this report."
   - A note at the top: "Do not share server addresses, tokens, passwords or other personal data."
4. Link the privacy policy (https://arthoriouss.github.io/skadi-releases/privacy/) in the form description.
5. Settings: keep responses private, enable e-mail notifications to yourself, never make results public.
6. Publish and copy the form URL (for example `https://tally.so/r/XXXXXX`).
7. Paste it in `docs/report/index.html`:
   ```js
   var TALLY_FORM_URL = "https://tally.so/r/XXXXXX";
   ```
   The page appends `?v=...&b=...&p=...&m=...&os=...&srv=...&cat=...&lang=...` itself. While the constant is empty, the button is disabled with "Coming soon".
8. Test with `report/?v=1.0.0-beta.19&b=60&p=webos&m=OLED55C9&os=webOS%204.5&srv=plex&cat=playback&lang=en` and check that the hidden fields are filled in a test submission.
