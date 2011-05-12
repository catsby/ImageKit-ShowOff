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


!SLIDE small
# ImageBrowserController.m #

    @@@ C
    - (IBAction) addImageButtonClicked:(id) sender
    {
        // static method that opens a file open dialog
        NSArray *path = openFiles(); 
     
        if(!path){
            return;
        }
       [NSThread 
        detachNewThreadSelector:@selector(addImagesWithPaths:) 
                       toTarget:self 
                     withObject:path];
    }

!SLIDE small
# ImageBrowserController.m #

    @@@ C
    - (void) addImagesWithPaths:(NSArray *) paths 
    {
      //  foreach path
      [self addImagesWithPath:path recursive:NO];
      
      ...  //   Back to you later 
    }


!SLIDE small
# ImageBrowserController.m #

    @@@ C
    - (void) addImagesWithPath:(NSString *) 
                path recursive:(BOOL) recursive
    {
      //  a bunch of recursive nonsense
      //  that optionally digs down through 
      //  through directories and eventually calls
      NSArray *content = [[NSFileManager defaultManager]
                           directoryContentsAtPath:path];

      [self addAnImageWithPath:
       [path stringByAppendingPathComponent:
                     [content objectAtIndex:i]]];
      //  on each path
      
    }

!SLIDE small
# ImageBrowserController.m #

    @@@ C
    - (void) addAnImageWithPath:(NSString *) path
    {
        MyImageObject *p;
     
        p = [[MyImageObject alloc] init];
        [p setPath:path];
        [mImportedImages addObject:p];
        [p release];
    }

!SLIDE small
# ImageBrowserController.m #

### Back in `addImagesWithPath:` ###

    @@@ C
    - (void) addImagesWithPaths:(NSArray *) paths 
    {
      ...   //  Aaaaaand we're back
      [self 
      performSelectorOnMainThread:@selector(updateDatasource)
                       withObject:nil
                    waitUntilDone:YES];
      
    }
