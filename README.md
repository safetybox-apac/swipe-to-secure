# Swipe to Secure

A standalone game for GitHub Pages. Includes the 30 existing scenarios and generated illustrations. No Google Apps Script, sign-up, administrator, rooms or player names are required.

## Publish on GitHub Pages

1. Extract `Swipe-to-Secure-Solo.zip` on your computer.
2. Open your game's GitHub repository, then **Add file → Upload files**.
3. Upload the contents of the extracted folder directly into the repository root. Include `index.html`, `app.js`, `audio.js`, both CSS files, `cards.csv`, `artwork.json`, `.nojekyll` and the entire `images` folder. Do not upload only the ZIP or put the application inside an extra folder.
4. Commit the files. In **Settings → Pages**, select **Deploy from a branch**, **main**, and **/(root)**. Save if these settings have changed.
5. Once deployment completes, use the website address shown in Pages. A project repository named `swipe-to-secure` normally uses `https://YOUR-USERNAME.github.io/swipe-to-secure/`.

Use a separate repository for this game to preserve your other games. This package has been tested locally; it has not been published to your account.

## Play

- Choose **Play on Desktop** or **Play on Phone**, read the instructions, and select **I'm ready**.
- A 3–2–1 countdown starts an individual, fixed **10-minute** session.
- Look at the picture and context. Swipe left for unsafe or right for safe. Buttons work in both modes; desktop also supports the left/right arrow keys during the decision step.
- Choose one of three actions. Feedback appears immediately, without a server request.
- Select the photo to enlarge it. On smaller screens, long content can scroll while decision controls remain accessible.
- Finish all scenarios, finish early, or let the timer expire to view your score. Reveal answers from the results screen.

The scenario and action-choice orders are randomized. Submitted decisions are locked. Each correct safe/unsafe decision earns **2 points**, and each correct action earns **1 point**, independently. The maximum is **90 points**. A correct swipe still earns 2 points if time expires before its action is selected. During play, the current card's points remain hidden until its action is selected.

Feedback in column I is shown for a correct swipe; column J is shown for an incorrect swipe. Action correctness is reported separately.

## Sound and loading

Music and effects are enabled by default and begin after a user interaction, subject to browser autoplay rules. The settings button contains sound controls only. Music preferences are saved on that device.

The ten bundled image packs prepare silently on the home page. If preparation is still running when the player selects **I'm ready**, the app waits before beginning the countdown. Images are served from the same GitHub Pages site, with no Google Drive photo requests. Each picture is labeled **AI generated — for illustration purposes only**.

Music stops while the tab is hidden, but the timer continues. Refreshing the same tab restores its session and original deadline. Sessions and scores are not centrally collected or synchronized across devices.

## Edit the database

Edit `cards.csv` in a spreadsheet and export it as UTF-8 CSV, preserving its headers and column order:

| Column | Content |
|---|---|
| A | Unique card ID |
| B | Image reference: `builtin:1` through `builtin:30`, or a local image path |
| C | Scenario context |
| D | Is Safe? — Yes or No |
| E | Management Action — retained for reference |
| F | Correct action |
| G | First incorrect action |
| H | Second incorrect action |
| I | Feedback for a correct swipe |
| J | Feedback for an incorrect swipe |

The supplied CSV preserves the existing 30 scenarios. Three action options must be distinct; required fields must not be blank.

`artwork.json` binds each built-in picture to its context, safety answer and correct action. The app checks this association to help prevent misleading picture/answer combinations. If you revise the meaning of those fields, review the illustration and update the associated artwork entry too, or replace it with a suitable new picture. Do not change an answer merely to bypass validation.

For a replacement picture, upload a JPG, JPEG, PNG or WebP to `images`, then set column B to a path such as `images/scenario-31.jpg`. Use a simple filename with letters, numbers, hyphens or underscores. Google Drive URLs are not supported by this static package. Local replacement images display without cropping.

Commit the updated CSV, artwork file and/or pictures to GitHub to publish changes. Reload the site and start a new session to use the updated database.

## Validation

Browser checks cover all 30 cards and ten image packs, desktop and phone layouts, pointer/keyboard decisions, independent 2+1 scoring, duplicate-click protection, immediate feedback, photo enlargement, refresh recovery, timer expiry, partial-card scoring and answer reveal.
