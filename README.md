going_native_examples
=====================

Example code for my going_native_talk

factorial.rb: trivial ruby inline example

levenshtein.rb: using ruby inline to do levenshtein distances

ffi_simple.rb: trivial ffi example

ffi_callback.rb: an example using callbacks

ffi_objc.rb: an example of invoking objective C using ffi

`Objc::NSFoo` is mapped to the `NSFoo` class (loaded via const missing). If you want classes outside Foundation or AppKit, adjust the ffi_lib call.

Methods can be called via `method_missing` or via `objc_send` for example to get the current date

    Objc::NSDate.objc_send(:date)

or

    Objc::NSDate.date

Use a hash to specify parameters for example

    Objc::NSString.stringWithCString "/Users/fred/Desktop/sound.mp3", encoding: 4 
    Objc::NSString.objc_send  stringWithCString: "/Users/fred/Desktop/sound.mp3", encoding: 4 

are equivalent to

    [NSString stringWithCString:"/Users/fred/Desktop/sound.mp3" encoding:4]


The following plays the sound at the indicated path:

    path = Objc::NSString.stringWithCString "/Users/fred/Desktop/sound.mp3", encoding: 4
    sound = Objc::NSSound.alloc.initWithContentsOfFile path, byReference: 1
    sound.play
