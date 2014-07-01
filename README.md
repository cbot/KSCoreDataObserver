KSCoreDataObserver
======
This is a tiny library to manage CoreData notifications in order to update the user interface when a NSManagedObject is either inserted, deleted or updated.

KSCoreDataObserver works a bit like NSFetchedResultsController, that is by observing the managed object context's NSManagedObjectContextObjectsDidChangeNotification.

Whenever a change event occurs, a block is called that allows you to update your user interface accordingly.

## Installation
Use CocoaPods to add KSCoreDataObserver to your project. Just add the following line to your Podfile.
```
pod 'KSCoreDataObserver', '~> 1.0.0'
```
## Example
```objective-c
KSCoreDataObserver *observer = [[KSCoreDataObserver alloc] init];
[observer setRequiredContext:aNSManagedObjectContext]; // optional to observe a specific NSManagedObjectContext
[observer setObservedObject:aManagedObject]; // optional to observe a specific NSManagedObject
[observer setMask:KSObserverTypeUpdated | KSObserverTypeDeleted]; // optional to only observe specific event types

observer.objectDidChangeBlock = ^(KSObserverType type, NSManagedObject *object, NSArray *changes) {
	// do whatever is necessary to update your user interface
};
```
