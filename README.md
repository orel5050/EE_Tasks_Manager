# EE Tasks Manager

Serve `index.html` through HTTP (for example, VS Code Live Server) or GitHub
Pages, rather than opening it through `file://`.

## Authentication

The login screen is visible by default and the dashboard stays hidden until
Firebase's `onAuthStateChanged` reports a signed-in user. Authentication buttons
remain disabled until the initial auth state is known. The header shows the
signed-in user's email (or display name) and provides logout.

Firebase restores saved logins on the same origin. Returning straight to the
dashboard is expected when a session is still valid. Use logout or a private
browser window to check the signed-out screen. Localhost and GitHub Pages have
separate saved sessions.

Enable the desired sign-in providers in Firebase Authentication. For Google
sign-in on GitHub Pages, add `orel5050.github.io` under Firebase Console >
Authentication > Settings > Authorized domains. Publish `firestore.rules` to
the configured Firebase project separately; GitHub Pages only serves static files.

## GitHub Pages updates

Commit and push the updated `index.html` to the branch/folder selected in the
repository's Settings > Pages, then wait for the Pages deployment to finish.
Pushing a file alone does not update a deployment configured for another source.
Open <https://orel5050.github.io/EE_Tasks_Manager/> and hard-refresh
(`Ctrl+Shift+R`) if necessary.

To verify a deployment, check the deployed page source for `id="app" hidden`,
`id="userEmail"`, and `id="logoutBtn"`. In a private window, only the login screen
should appear. After login, the dashboard, account identity, and logout button
should appear; logout should return to the login screen.
