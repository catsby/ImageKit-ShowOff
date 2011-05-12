!SLIDE small
# ImageBrowserItem.h #

    @@@ C
    @interface ImageBrowserItem: NSObject {
        NSString * mPath;
    }

    @property (nonatomic, copy) NSString *mPath;

    - (NSString *)imageRepresentationType
    - (id)  imageRepresentation
    - (NSString *) imageUID
    @end

!SLIDE small
# ImageBrowserItem.m #

    @@@ C

    @synthesize mPath;

    - (NSString *)  imageRepresentationType
    {
        return IKImageBrowserPathRepresentationType;
    }
     
    - (id)  imageRepresentation
    {
        return mPath;
    }
     
    - (NSString *) imageUID
    {
        return mPath;
    }

