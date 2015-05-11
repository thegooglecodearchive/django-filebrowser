# Basic Installation #

  1. **Install the FileBrowser**
> > Install the FileBrowser anywhere on your python-path. I´m personally using the project-directory.
```
svn checkout http://django-filebrowser.googlecode.com/svn/trunk/filebrowser/ filebrowser
```
  1. **Copy/Symlink Media**
> > Copy the folder /media somewhere to your media-directory and change URL\_FILEBROWSER\_MEDIA accordingly.<br>
<blockquote>Alternatively, you may want to use a symlink from your media-directory.<br>
</blockquote><ol><li><b>Add filebrowser to your INSTALLED APPS.</b>
<blockquote>Open your projects settings-file (settings.py) and add the filebrowser to your INSTALLED APPS.<br>
</blockquote></li><li><b>Change filebrowser settings.py</b>
<blockquote>Either change settings.py or overwrite the filebrowser settings in your project settings-file. See "Available Settings".<br>
</blockquote></li><li><b>Change your urls.py</b>
<blockquote>Add the following line BEFORE the admin-urls:<br>
<pre><code>(r'^admin/filebrowser/', include('filebrowser.urls')),<br>
</code></pre>
</blockquote></li><li><b>Add the FileBrowser to your Admin Navigation</b>
<blockquote>With using Grappelli, you can add the FileBrowser to your Admin Index Page by changing the Sidebar-Navigation (the FileBrowser is already part of the Grappelli fixtures).<br>
</blockquote></li><li>That's it.</li></ol>

<hr />
<b>IMPORTANT: About 90% of the problems installing the filebrowser are related to wrong URLS and/or PATHS. So, please read through <a href='http://code.google.com/p/django-filebrowser/wiki/Settings'>Available Settings</a> and check everything with either <i>URL</i> or <i>PATH</i> carefully (especially when using TinyMCE).</b>

<h3>Check yourself before you...create an issue</h3>

good way to do this (by alper.cugun):<br>
<br>
<pre><code>$ python manage.py shell<br>
&gt;&gt;&gt; import django.conf.settings<br>
&gt;&gt;&gt; import filebrowser.settings<br>
</code></pre>

Now for all the relevant settings in filebrowser (and maybe also some in django), call them up in the prompt to see what they end up like:<br>
<br>
<pre><code>&gt;&gt;&gt; filebrowser.settings.DEFAULT_URL_TINYMCE<br>
'/media/tinymce/jscripts/tiny_mce/'<br>
</code></pre>

And check for both URLs and paths if those are reachable existing locations and that they<br>
actually contain the things they are supposed to.<br>
<hr />