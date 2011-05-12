!SLIDE small
# ImageBrowserController.h #

    @@@ C
    @interface ImageBrowserController : NSWindowController {
     
        IBOutlet id mImageBrowser;
        NSMutableArray * mImages;
        NSMutableArray * mImportedImages;
    }

    - (IBAction) addImageButtonClicked:(id) sender;
    @end

!SLIDE small
# ImageBrowserController.m #

    @@@ C
    - (void) awakeFromNib
    {
        mImages = [[NSMutableArray alloc] init];
        mImportedImages = [[NSMutableArray alloc] init];
     
        [mImageBrowser setAnimates:YES];
    }
    - (void) updateDatasource
    {
        [mImages addObjectsFromArray:mImportedImages];
        [mImportedImages removeAllObjects];
        [mImageBrowser reloadData];
    }


!SLIDE small
# ImageBrowserController.m #

### Data Source Methods ###
    
    @@@ C
    - (int) numberOfItemsInImageBrowser:(IKImageBrowserView *) view
    {
        return [mImages count];
    }
     
    - (id) imageBrowser:(IKImageBrowserView *) view itemAtIndex:(int) index
    {
        return [mImages objectAtIndex:index];
    }
