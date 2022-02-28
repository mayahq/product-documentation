# Changelog

Find latest releases [here](https://github.com/mayahq/maya-desktop/releases).

### v0.13.1-beta

2022/1/28

* \[New] Task manager on dashboard long running repeatable tasks (uses Maya Bot Utils module)
* \[New] Maya Releases for Windows now available (finally!)
* \[New] Share and install automation collections with single link to a valid json file hosted anywhere
* \[New] Crash recovery and notification for unrecovarable failures in automation workspace
* \[Enhance] In editor store and dashboard accessibility buttons
* \[Enhanced] Updated Maya Browser Automation extension for browsers for easier automation

### v0.13.0-beta

2021/12/18

* \[New] Reset your app to factory from settings
* \[New] Import and install any Maya compatible skill collection straight into the editor
* \[New] Quick export and share your skill collection directly as JSON with any other Maya user
* \[New] Login through your saved password for Maya in your browser
* \[New] Search for nodes and install corresponding modules from the editor directly
* \[New] Hardened security for your locally saved credentials
* \[New] Fallback implemented if device doesn't have keychain/keyring access
* \[Enhance] New views added to store: Skill packs are now Collections, Intents are now Commands
* \[Fix] App intermittently requires logging out to continue working

### v0.12.4-beta

2021/10/20

* \[Enhance] No more node and workspaces limits in free tier
* \[Fix] OAuth 2.0 configurations refresh token architecture improved for dynamic token validity
* \[Enhance] Now install external Node RED compatible modules to Maya workspaces and save in library
* \[Enhance] Scroll through all results on custom search type response placeholders in command bar
* \[New] Preview dashboard type skills from Dashboard option in Editor Menu drawer
* \[Enhance] Now sign up and register with Maya without needing to apply for waitlist, ask for your invite code with your use case
* \[New] Offline check ribbon to inform whether the application is offline

###

### v0.12.3-beta

2021/10/06

* \[Fix] Bug fix which minimized studio on opening native commands from command bar
* \[Fix] Setup Wizard module list overflows for more than four modules selected
* \[Enhance] Store and library views made responsive to window resize
* \[Enhance] Cleaner skill flow animations in Maya Skill Generator
* \[New] Upgrade to Maya Premium with easy to use subscription pricing

### v0.12.2-beta

2021/09/21

* \[New] Install unlimited Store skillpacks in Default Runtime
* \[New] Upgrade to premium tier to use unlimited nodes, build your own skills and get support
* \[New] Import your Google contacts and use for phone and email placeholders from Settings
* \[New] Dock icon visible for MacOS
* \[New] Release now available for Mac Silicon
* \[Enhance] Autoselect first recommendation on service search recommendations
* \[Enhance] Refocus back to previous application after using command bar

### v0.12.1-beta

2021/08/28

* \[Enhance] Setup Wizard experience for cleaner and more understandable flow
* \[Enhance] Recommendation experience in various Maya skills
* \[Fix] Crash on re-login
* \[Fix] More edge case handled in module profile configurations

### v0.12.0-beta

2021/08/23

* \[New] Manage all module configurations from Settings
* \[Fix] Reliable handling of error in command execution
* \[Fix] Reliable and secure token updates for OAuth services
* \[Fix] Command bar card section history
* \[Enhance] Intercom messenger integrated for live chat support

### v0.11.5-beta

2021/08/17

* \[New] Discover native Maya commands in command bar and get started quick
* \[New] New Store layout with category based search functions
* \[Enhance] Reliable handling of error in command execution
* \[Enhance] Reliable and secure token updates for OAuth services

### v0.11.4-beta

2021/07/28

* \[Enhance] New command bar experience with new UI, action shortcuts and feedback
* \[Enhance] Get a default runtime to install all your store skills on
* \[Enhance] Maya Web Automation Extension gets a more user friendly permission management
* \[Fix] Bug preventing refresh of OAuth tokens

### v0.11.3-beta

2021/07/13

* \[Enhance] Removed extra steps in brain runtime creation + skill installation
* \[Enhance] Better search recommendations on command bar
* \[Enhance] More stability to command bar access experience
* \[Enhance] First installation Setup Wizard experience improvement
* \[Fix] Memory leak preventions from cascading crash
* \[New] Installed skillpacks visible on home screen
* \[New] New Tray menu
* \[New] Search feature for skills/modules within store

### v0.11.2-beta

2021/06/24

* \[Fix] UX focus issues on clicking on command bar results
* \[Fix] Fixed fullscreen traffic light for MacOS users.
* \[Fix] Screen switching inconsistencies on opening and closing command bar.
* \[New] The default command bar invocation hotkey is changed to Alt/Option (⌥) + Space
* \[Enhance] Faster application network calls

### v0.11.1-beta

2021/06/18

* \[Fix] Module installation error resolved
* \[Fix] UX inconsistencies in new Setup Wizard for first time users
* \[New] Added Setup Wizard button to let users restart setup wizard
* \[Enhance] Security patch

### v0.11.0-beta

2021/06/13

* \[New] Improved setup wizard for first time users to educate and set up Maya for them.
* \[New] Icons support in the Maya Search bar recommendation
* \[New] Zoom Meetings integration and ready to use skill on the marketplace
* \[New] Developer only feature to try out auto-generation of skills (experimental)
* \[New] Forgot password on the login page setup
* \[New] Updated Google Drive module with new node to download files and add them to your workflow
* \[Fix] Brain runtime editor freeze issues resolved
* \[Enhance] The application download and install size reduced to more than 50% from v0.10.4-hotfix-1
* \[Skills] New skills added to the

### v0.10.4-hotfix-1

2021/05/18

* \[Fix] NPM Integrated Module installation fixed
* \[Fix] Autostart on interrupted brain runtimes from a previous session fixed
* \[Feature] Control your default Chromium based browser with Web-Automation-Module integration and Maya Web Automation Extension now published on Chrome Web Store
* \[New] New integrations for Google Calendar and Google Drive

### v0.10.4-beta

2021/05/12

* \[Enhance] String queries on Search Bar defaults showing google search recommendations
* \[Enhance] Updated styles to display list of skills and command to invoke them
* \[Feature] Control your default Chromium based browser with Web-Automation-Module integration and Maya Web Automation Extension
* \[Feature] Integrated NPM Support removes the need to setup NVM and NodeJS environment for installation
* \[Feature] More Security: All user credentials for 3rd party integrations are now stored in OS Keychain
* \[Enhance] Faster brain runtime creation with pre-filled default names

### v0.10.3-beta

2021/04/10

* \[Fix] Pressing esc on loading doesn't hide command bar.
* \[Fix] Scrollbar styling updated to be consistent
* \[Fix] Setup wizard now updates environment variables for both bash and zsh in MacOS
* \[Fix] Update notification bar now doesn't overlay on action buttons

### v0.10.2-beta

2021/04/08

* \[Fix] Fixes NPM install errors on Mac devices with varying defaults shells.
* \[Fix] Setup Wizard screen appears whenever Setup Wizard quick link is pressed in home screen.
* \[Fix] Brain runtime doesn't auto-start on creation
* \[Fix] Deleting a brain removed the brain access tab
* \[Enhance] Loading skeletons removed when library is empty, shows empty list
* \[Enhance] Hide Maya command bar on hitting Esc when input empty
* \[Fix] Form validation on profile config creation

### v0.10.1-beta

2021/04/05

* \[Feature] New cooler loading screen for app bootup
* \[Fix] Fixed a reported memory leak and improved stability
* \[Enhance] Updates sections improved:
  * Items from list get removed after successful update
  * Feedback toast for update completion/failure
* \[Fix] Fix on Deploy button to update intent commands
* \[Enhance] UX improvement in Maya Search bar
* \[Fix] App quits completely on clicking red button on traffic light
* \[Enhance] New designs and images on the first time set up screen
* \[Feature] Skills shared over web link can be opened in Electron app through browser deeplink
* \[Enhance] Overall theme is slightly darker than before
* \[Feature] Landing on Updates section does 'Check for Updates' sections
* \[Fix] You can now create new brains while installing skillpack or modules from library/store.

### v0.10.0-beta

2021/03/31

* \[Fix] Maya Search background glitch fixed
* \[Fix] Multiple instances of app opening on MacOS resolved
* \[Fix] Graceful exit to solve `Object has been destroyed` error
* \[Feature] Opening the editor starts the runtime if it has not started
* \[Fix] CSS fixes for viewports on large screens, scrolls added to category sections in store
* \[Feature] Unlisted publishing of skills added to share skills privately
* \[Fix] Updating library item doesn't create new entry anymore
* \[Enhance] Configure Profile button UI and UI flow improved
* \[Support] Logging added to application for identifcation and support
* \[Feature] Visual feedback tool usersnap integrated to obtain user feedback anywhere in the app with screenshot
* \[Support] Usage analytics added to collect and improve on crash and drops
