# The FileObject #
New in Version 3.0: When browsing a directory on the server, you get a FileObject (see base.py) for every file within that directory.

Any FileObject has the following attributes:
  * **filename**
  * **filetype** (as defined in EXTENSIONS)
  * **filesize** (output with filesizeformat)
  * **extension** (as defined in EXTENSIONS)
  * **date** (getmtime)
  * **datetime** (datetime object)

  * **path** (relative to MEDIA\_ROOT)
  * **path\_relative** (=path)
  * **path\_full** (including MEDIA\_ROOT)
  * **url\_relative** (=path)
  * **url\_full** (including MEDIAURL)
  * **url\_save** (URL used for the FileBrowseField)
  * **url\_thumbnail** (Full URL for the Admin-Thumbnail)

An Image has additional attributes:
  * **dimensions** (tuple)
  * **orientation** (either "landscape" or "portrait")
  * **width** (in px)
  * **height** (in px)

A Folder has additional attributes:
  * **is\_empty** (True/False)

Set DEBUG to True in order to see the FileObject values.