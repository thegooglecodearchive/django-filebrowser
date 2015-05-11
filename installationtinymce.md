# Using the FileBrowser with TinyMCE #

You can also replace the TinyMCE Image/File Manager with the FileBrowser.
What you have to do is a **FileBrowser Callback**. There´s an example in /media/js/ called **TinyMCEAdmin.js** (a TinyMCE Configuration File). You can copy the FileBrowserCallback to your own file, take a look at http://wiki.moxiecode.com/index.php/TinyMCE:Custom_filebrowser or just use TinyMCEAdmin.js.

  1. **Just add these lines to your AdminModel**
```
    class Media:
        js = ['/path/to/tinymce/jscripts/tiny_mce/tiny_mce.js', '/path/to/media/admin/filebrowser/js/TinyMCEAdmin.js',]
```