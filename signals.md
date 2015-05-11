# Signals #

The FileBrowser sends a couple of different signals:
  * **filebrowser\_pre\_upload**
> > This Signal is sent _before_ a an Upload starts.<br>
<blockquote>kwargs: path, file<br>
</blockquote><ul><li><b>filebrowser_post_upload</b>
<blockquote>This Signal is sent <i>after</i> an Upload has finished.<br>
kwargs: path, file<br>
</blockquote></li><li><b>filebrowser_pre_delete</b>
<blockquote>This Signal is sent <i>before</i> an Item (File, Folder) is deleted.<br>
kwargs: path, filename<br>
</blockquote></li><li><b>filebrowser_post_delete</b>
<blockquote>This Signal is sent <i>after</i> an Item (File, Folder) has been deleted.<br>
kwargs: path, filename<br>
</blockquote></li><li><b>filebrowser_pre_createdir</b>
<blockquote>This Signal is sent <i>before</i> a new Folder is created.<br>
kwargs: path, dirname<br>
</blockquote></li><li><b>filebrowser_post_createdir</b>
<blockquote>This Signal is sent <i>after</i> a new Folder has been created.<br>
kwargs: path, dirname<br>
</blockquote></li><li><b>filebrowser_pre_rename</b>
<blockquote>This Signal is sent <i>before</i> an Item (File, Folder) is renamed.<br>
kwargs: path, filename<br>
</blockquote></li><li><b>filebrowser_post_rename</b>
<blockquote>This Signal is sent <i>after</i> an Item (File, Folder) has been renamed.<br>
kwargs: path, filename</blockquote></li></ul>

Example for using these Signals:<br>
<pre><code>from filebrowser.views import filebrowser_pre_upload, filebrowser_post_upload<br>
<br>
def pre_upload_callback(sender, **kwargs):<br>
    """<br>
    Receiver function called before an upload starts.<br>
    """<br>
    print "Pre Upload Callback"<br>
    print "kwargs:", kwargs<br>
filebrowser_pre_upload.connect(pre_upload_callback)<br>
<br>
def post_upload_callback(sender, **kwargs):<br>
    """<br>
    Receiver function called each time an upload has finished.<br>
    """<br>
    print "Post Upload Callback"<br>
    print "kwargs:", kwargs<br>
    # You can use all attributes available with the FileObject<br>
    # This is just an example ...<br>
    print "Filesize:", kwargs['file'].filesize<br>
    print "Orientation:", kwargs['file'].orientation<br>
    print "Extension:", kwargs['file'].extension<br>
filebrowser_post_upload.connect(post_upload_callback)<br>
</code></pre>

Another example is here (it´s a contribution by a user, so I haven´t checked the code):<br>
<a href='http://www.djangosnippets.org/snippets/1893/'>http://www.djangosnippets.org/snippets/1893/</a>