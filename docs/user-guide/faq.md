# Frequently Asked Questions

### Can I use trees for organizing my pictures and albums? ###

Except in *Library > Originals* and for object classification in *Labels*, PhotoPrism does not
support hierarchically organized content for a number of reasons:

First, there are many tools (including Windows Explorer and Mac OS Finder) that already browse folders in such a way.

A common UX challenge is dealing with namespaces.
For example, the album "Berlin" may exist 5 times in different parts of a tree.
To avoid ambiguities, simple input fields need to be replaced with a tree browser that 
shows the complete context.
This is especially difficult on mobile screens.

Personal albums can typically be browsed by time, with optional filters for more specific results.
This is different in Enterprise asset management, where trees are required to manage 
responsibilities & [permissions](https://github.com/photoprism/photoprism/issues/455#issuecomment-675859270). 
We might do a special release for professional users later. 

While you have complete freedom with organizing your original files and folders,
we don't think trees should be an integral part of our user interface.
Most users won't be able to sort their memories in a strictly hierarchical way 
and prefer to explore them in multiple dimensions instead.

### What's the difference between keywords and labels? ###

Keywords contain a list of search terms extracted from metadata, file names, and other sources 
like geodata. Pictures with matching keywords automatically show up in related *Labels*. 

Although related, keywords and labels serve different purposes:

* **Labels** may have parent categories and are primarily used for classification, like "animal", "cat", or "boat". 
  Duplicates and ambiguities should be avoided.
* **Keywords** are primarily used for searching. They may include similar terms and translations,
  like "kitten", "kitty", and "cat".

### Which file types are supported? ###

PhotoPrism's primary image file format is JPEG.
While indexing, a JPEG sidecar file may automatically be created for RAW, HEIF, TIFF, PNG, BMP, 
and GIF files. It is required for classification and resampling.

Support for specific RAW formats depends on the runtime environment and configuration. PhotoPrism may use 
[Darktable](https://www.darktable.org/) and [RawTherapee](https://rawtherapee.com/) for RAW to JPEG conversion. 
On Mac OS, [Sips](https://ss64.com/osx/sips.html) can be used as well.

We support all common video types.
You should configure PhotoPrism to automatically create JSON sidecar files so that
video metadata like location and duration can be indexed.

You're welcome to open an issue if you experience issues with a specific file format.

### Some files seem hidden, where are they? ###

If the [quality filter](organize/review.md) is enabled, you might find them in *Photos > Review*. Otherwise, their
format may not be supported, they may be corrupted, or they may be stacked with other files if their name, 
exact date & location, or unique image ID indicate they belong to the same photo. You may then unstack 
them if this happened by mistake e.g. because of bad metadata.

### Why are some files stacked although I disabled "Stack Sequences" in Settings? ###

Files with the same *XMP Instance ID* or *Unique Image ID* as well 
as images with the exact same time and location will always be stacked. These are considered identical, not sequences 
of related files based on their file names. Sidecar files will also always be stacked as that's their purpose.

### Why do some pictures have an odd date like 01/01/1980? ###

This may happen in case there was an issue with your camera's settings when the photo was taken.
While the date can easily be changed in the [edit dialog](organize/edit.md), this only updates the index 
without modifying your originals.

To fix the date directly in your image or video files, please use other applications
like Photoshop, or Exiftool, and re-index your library.

### How can I permanently delete files? ###

As we currently don't modify originals to avoid accidental data loss and conflicts with other applications, 
you may only "soft delete" pictures by moving them to *Photos > Archive* using the context menu (if enabled in Settings).

Permanently deleting files for freeing up storage will be implemented in a later release,
see [Use trashcan to physically delete files after confirmation #167](https://github.com/photoprism/photoprism/issues/167).

When deleting files manually, or using other applications, make sure to re-index your library 
(or run `photoprism purge` in a terminal).

### I already indexed some files. Why are Folders, Calendar and Moments still empty? ###
Folders, Calendar and Moments are populated at the end of the indexing process.

### Does edit the docs work? ###
