# React Code Guide

## Comments

Comments are use to explain the 'why' behind the code. The 'how' can be inferred from looking at the code. The reasons behind choices are important to include in your comments. In a react project we follow some simple rules for commenting to keep files consistent. 

Imports should be organised by comments (short name - description). Here are some popular import groups:

```
    /* NPM - Node Package Manage */
    import React from "react";
    /* Redux - State Management */ (or other stare management library)
    ...
    /* Config - Local Configuration */
    ...
    /* Utils - Project Utilities */
    ...
    /* Components */
    ...
    /* Constants */
```

Comments should be used to structure variables at the top of each component:

```
    /* Redux */
    const theme = useSelector(state => getOrganisationTheme(state));
    const dispatch = useDispatch();
    /* Custom Hooks */
    const analytics = useAnalytics({ prefix: SCREEN_NAME });
    /* Refs */
    const actionTipRef = useRef(null);
    /* State */
    const [isRefreshing, setIsRefreshing] = useState(false);
    const [isPaginating, setIsPaginating] = useState(false);
    /* Variables */
    const isUserEmpty = _isEmpty(referralUrl);
    const isReferralsEmpty = _isEmpty(referrals);
    /* Colors */
    const baseColor = _get(theme, "base", "#F91276");
```

Comments can be used to break down the control flow of a program to make it more readable.  It to note that 'why' comments should be used instead, if applicable e.g.

```
    // Used to close the array in our JavaScript file
    iconsJavascriptContent = iconsJavascriptContent + "]";
    
    // We use object assign, this takes the existing icons, our primary icon, and icons folder and updates them
    plistObject["CFBundleIcons"]["CFBundleAlternateIcons"] = 
        Object.assign(plistObject["CFBundleIcons"]["CFBundleAlternateIcons"], PRIMARY_ICON, icons);
    
    // Build the plist object back into an XML list
    const result = plist.build(plistObject);
    
    // Write the modified plist file back to source
    try {
        fs.writeFileSync(PLIST_PATH, result);
        terminal.white(`\n The plist file ${PLIST_PATH} was updated with new app icons. \n`);
    } catch(e) {
        return terminal.red(err);
    }
    
    // Write to the JavaScript file used in the app to keep track of our active icons
    try {
        fs.writeFileSync(JS_FILE_PATH, iconsJavascriptContent);
    } catch(e) {
        return terminal.red(err);
    }
```