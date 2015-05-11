# Release Notes #

### 3.0 (2009-11-12) ###

  * New FileObject.
  * Versions are generated "on the fly" - generating Versions on Upload is no longer necessary/possible.
  * New URL configuration: Directories are now passed via query-string. So, the restriction for folder-names (DISALLOWED\_FOLDER\_NAMES) is gone.
  * FileBrowseField returns a FileObject (instead of a string).
  * New attribute "format" for FileBrowseField. With using "format", it´s possible to limit the selection to different filetypes.
  * Versions/Thumbnails can be stored in a seperate directory.
  * Overwrite files on Upload (filename is checked via ajax).
  * sorl-thumbnail is no longer needed.
  * DEBUG-Mode in order to display FileObjects in the Admin-Interface.
  * Some settings have changed (see Available Settings).
  * New Version-settings should be more flexible.
  * Code is much cleaner (although far from hugely satisfying).
  * Using Uploadify (including an Upload Progress Bar and better error-handling).
  * Signals.