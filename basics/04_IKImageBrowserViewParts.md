!SLIDE bullets smbullets pretty-uls mini-browser
## IKImageBrowserDataSource ##

### Required: ###

- `numberOfItemsInImageBrowser:`  
- `imageBrowser:itemAtIndex:`

### Optional: ###

- `imageBrowser:removeItemsAtIndexes:`
- `imageBrowser:moveItemsAtIndexes:toIndex:`
- `numberOfGroupsInImageBrowser:`
- `imageBrowser:groupAtIndex:`

!SLIDE bullets smbullets pretty-uls mini-browser
## IKImageBrowserItem ##

### Required: ###

- `imageRepresentationType`  
- `imageUID`
- `imageRepresentation`

### Optional: ###

- `imageVersion`
- `imageTitle`
- `imageSubtitle`
- `isSelectable`

!SLIDE bullets smbullets pretty-uls
## IKImageBrowserDelegate ##

### Optional: ###

- `imageBrowser:backgroundWasRightClickedWithEvent:`
- `imageBrowser:cellWasRightClickedAtIndex:withEvent:`
- `imageBrowser:cellWasDoubleClickedAtIndex:`
- `imageBrowserSelectionDidChange:`
