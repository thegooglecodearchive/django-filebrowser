# Available Settings #

All Settings can be defined in your projects settings-file or the FileBrowsers settings-file (settings.py). When using the projects settings-file, you have to use the prefix "FILEBROWSER" for every setting (e.g. FILEBROWSER\_MEDIA\_URL instead of MEDIA\_URL).
### DEBUG ###
Set to True in order to get an additional column with the fileobjects data.
```
DEBUG = getattr(settings, "FILEBROWSER_DEBUG", False)
```
### MAIN URL/PATH SETTINGS ###
The absolute path to the directory that holds your media-files.
```
MEDIA_ROOT = getattr(settings, "FILEBROWSER_MEDIA_ROOT", settings.MEDIA_ROOT)
```
URL that handles the media served from MEDIA\_ROOT.
```
MEDIA_URL = getattr(settings, "FILEBROWSER_MEDIA_URL", settings.MEDIA_URL)
```
Main FileBrowser Directory. This has to be a directory within MEDIA\_ROOT. Leave empty in order to browse all files under MEDIA\_ROOT.
```
DIRECTORY = getattr(settings, "FILEBROWSER_DIRECTORY", 'uploads/')
```
### FILEBROWSER\_MEDIA & TINYMCE\_MEDIA ###
The URL and Path to your FileBrowser media-files. You have to change this settings, if you install the media-files of the FileBrowser outside your admin-media directory.
```
URL_FILEBROWSER_MEDIA = getattr(settings, "FILEBROWSER_URL_FILEBROWSER_MEDIA", "/media/filebrowser/")
PATH_FILEBROWSER_MEDIA = getattr(settings, "FILEBROWSER_PATH_MEDIA", os.path.join(settings.MEDIA_ROOT, 'filebrowser/'))
```
The URL to your TinyMCE Installation. You have to change this settings, if you install TinyMCE outside your admin-media directory.
```
URL_TINYMCE = getattr(settings, "FILEBROWSER_URL_TINYMCE", settings.ADMIN_MEDIA_PREFIX + "tinymce/jscripts/tiny_mce/")
PATH_TINYMCE = getattr(settings, "FILEBROWSER_PATH_TINYMCE", settings.ADMIN_MEDIA_PREFIX + "tinymce/jscripts/tiny_mce/")
```
### EXTENSIONS & SELECT\_FORMATS ###
Allowed Extensions for File Upload. Please be aware that there are Icons for the default extension settings. If you rename "Audio" to "Music", you also have to rename the Audio-Icon within the img-directory.
```
EXTENSIONS = getattr(settings, "FILEBROWSER_EXTENSIONS", {
    'Folder': [''],
    'Image': ['.jpg','.jpeg','.gif','.png','.tif','.tiff'],
    'Video': ['.mov','.wmv','.mpeg','.mpg','.avi','.rm'],
    'Document': ['.pdf','.doc','.rtf','.txt','.xls','.csv'],
    'Audio': ['.mp3','.mp4','.wav','.aiff','.midi','.m4p'],
    'Code': ['.html','.py','.js','.css']
})
```
Set different Options for selecting elements from the FileBrowser.
```
SELECT_FORMATS = getattr(settings, "FILEBROWSER_SELECT_FORMATS", {
    'File': ['Folder','Document',],
    'Image': ['Image'],
    'Media': ['Video','Sound'],
    'Document': ['Document'],
    # for TinyMCE we also have to define lower-case items
    'image': ['Image'],
    'file': ['Folder','Image','Document',],
})
```
### VERSIONS\_BASEDIR & VERSIONS ###
```
VERSIONS_BASEDIR = getattr(settings, 'FILEBROWSER_VERSIONS_BASEDIR', '_versions_')
```
```
VERSIONS = getattr(settings, "FILEBROWSER_VERSIONS", {
    'fb_thumb': {'verbose_name': 'Admin Thumbnail', 'width': 60, 'height': 60, 'opts': 'crop upscale'},
    'thumbnail': {'verbose_name': 'Thumbnail (140px)', 'width': 140, 'height': '', 'opts': ''},
    'small': {'verbose_name': 'Small (300px)', 'width': 300, 'height': '', 'opts': ''},
    'medium': {'verbose_name': 'Medium (460px)', 'width': 460, 'height': '', 'opts': ''},
    'big': {'verbose_name': 'Big (620px)', 'width': 620, 'height': '', 'opts': ''},
    'cropped': {'verbose_name': 'Cropped (60x60px)', 'width': 60, 'height': 60, 'opts': 'crop'},
    'croppedthumbnail': {'verbose_name': 'Cropped Thumbnail (140x140px)', 'width': 140, 'height': 140, 'opts': 'crop'},
})
```
```
ADMIN_VERSIONS = getattr(settings, 'FILEBROWSER_ADMIN_VERSIONS', ['thumbnail','small', 'medium','big'])
ADMIN_THUMBNAIL = getattr(settings, 'FILEBROWSER_ADMIN_THUMBNAIL', 'fb_thumb')
```
### OPTIONAL SETTINGS ###
**SAVE\_FULL\_URL:**True to save the URL including MEDIA\_URL to your model fields or False (default) to save path relative to MEDIA\_URL.
```
SAVE_FULL_URL = getattr(settings, "FILEBROWSER_SAVE_FULL_URL", True)
```
**STRICT\_PIL:** If set to True, then FileBrowser will not try to import a mis-installed PIL.
```
STRICT_PIL = getattr(settings, 'FILEBROWSER_STRICT_PIL', False)
```
**IMAGE\_MAXBLOCK:** see http://mail.python.org/pipermail/image-sig/1999-August/000816.html
```
IMAGE_MAXBLOCK = getattr(settings, 'FILEBROWSER_IMAGE_MAXBLOCK', 1024*1024)
```
**EXCLUDE:**
```
EXTENSION_LIST = []
for exts in EXTENSIONS.values():
    EXTENSION_LIST += exts
EXCLUDE = getattr(settings, 'FILEBROWSER_EXCLUDE', (r'_(%(exts)s)_.*_q\d{1,3}\.(%(exts)s)' % {'exts': ('|'.join(EXTENSION_LIST))},))
```
**MAX\_UPLOAD\_SIZE:** Max. Upload Size in Bytes.
```
MAX_UPLOAD_SIZE = getattr(settings, "FILEBROWSER_MAX_UPLOAD_SIZE", 10485760)
```
**CONVERT\_FILENAME:** replace spaces and convert to lowercase
```
CONVERT_FILENAME = getattr(settings, "FILEBROWSER_CONVERT_FILENAME", True)
```
**LIST\_PER\_PAGE:** control how many items appear on each paginated browse-list.
```
LIST_PER_PAGE = getattr(settings, "FILEBROWSER_LIST_PER_PAGE", 50)
```
**DEFAULT\_SORTING\_BY:** set the default sorting attribute.
```
DEFAULT_SORTING_BY = getattr(settings, "FILEBROWSER_DEFAULT_SORTING_BY", "date")
```
**DEFAULT\_SORTING\_ORDER:** asc, desc.
```
DEFAULT_SORTING_ORDER = getattr(settings, "FILEBROWSER_DEFAULT_SORTING_ORDER", "desc")
```