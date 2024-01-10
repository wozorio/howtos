# Hide native tabs with Tree Style tabs for Firefox

As the workspace for developers has moved almost entirely into the browser, browser extensions have become an integral part for customizing the workflow. Recently, I started to the use the Tree Style addons: https://addons.mozilla.org/en-US/firefox/addon/tree-style-tab/

When using this extension, the native tab bar becomes obsolete. The following part of the post is an instruction on how to hide the native tab bar (which is a bit difficult).

1. Type `about:support` into the address bar.
1. Look for the Profile Folder entry and click on Open folder.
1. Create a file named chrome/userChrome.css in the directory:
   ```bash
   mkdir chrome && touch chrome/userChrome.css
   ```
1. Populate the file with the following CSS code:
   ```javascript
   #main-window[tabsintitlebar="true"]:not([extradragspace="true"]) #TabsToolbar > .toolbar-items {
    opacity: 0;
    pointer-events: none;
   }
   #main-window:not([tabsintitlebar="true"]) #TabsToolbar {
      visibility: collapse !important;
   }
   #sidebar-box[sidebarcommand="treestyletab_piro_sakura_ne_jp-sidebar-action"] #sidebar-header {
    display: none;
   }
   .tab {
    margin-left: 1px;
    margin-right: 1px;
   }
   ```
1. Then type `about:config` into the address bar and set `toolkit.legacyUserProfileCustomizations.stylesheets` to `true`.
1. Restart Firefox

Now the native tab should be hidden. To reset the change simply remove the userChrome.css file.
