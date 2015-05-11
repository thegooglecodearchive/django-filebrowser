# Using the FileBrowseField #

The FileBrowseField is a Model field (see http://docs.djangoproject.com/en/dev/ref/models/fields/#field-types for other field types) used to select a File/Document/Image/Folder from your Media Server.

  1. **Define your models like this**
```
from filebrowser.fields import FileBrowseField

class Publication(models.Model):
    ...
    image = FileBrowseField("Image", max_length=200, blank=True, null=True)
    image_initialdir = FileBrowseField("Image (Initial Directory)", max_length=200, directory="images/", blank=True, null=True)
    image_extensions = FileBrowseField("Image (Extensions)", max_length=200, extensions=['.jpg'], help_text="Only jpg-Images allowed.", blank=True, null=True)
    image_format = FileBrowseField("Image (Format)", max_length=200, format='Image', blank=True, null=True)
    pdf = FileBrowseField("PDF", max_length=200, directory="documents/", extensions=['.pdf'], format='Document', blank=True, null=True)
    ...
```

### Attributes for the FileBrowseField ###
  * **max\_length**
> > Since the FileBrowseField is basically a CharField, you have to define max\_length.
  * **directory**
> > Subdirectory of DIRECTORY (see settings.py). If DIRECTORY is not defined, subdirectory of MEDIA\_ROOT. Do not prepend a slash.
  * **extensions**
> > List of Extensions allowed for this Field. Users will get an error message ("Extension not allowed.") if the selected File has an extension not listed here. Extensions are automatically converted to lowercase - therefore, you don´t have to define '.JPG' and '.jpg', but only '.jpg'.
  * **format**
> > Use this attribute to restrict selection to specific filetypes. E.g., if you use **format='Image'**, only Images can be selected from the FileBrowser. Note: The Format has to be defined within SELECT\_FORMATS.

### Image Preview ###
The Thumbnail will automatically be generated. Clicking on the Thumbnail below the FileBrowseField will open the Image in a new window/tab.

### FileBrowseField in Templates ###
When using a FileBrowseField, you´ll get a FileObject back (see FileObject).

With the above Publication-Model, you can use
```
{{ publication.image }}
```
to output the contents of your image-field. For example, this could result in something like "uploads/images/myimage.jpg".

Now, if you want to actually display the Image, you write:
```
<img src="{{ publication.image }}" class="ImageClass" />
```

More complicated, if you want to display "Landscape" Images only (I know, bad example):
```
{% ifequal publication.image.image_orientation "landscape" %}
    <img src="{{ publication.image }}" class="ImageClass" />
{% endifequal %}
```

### Showing Thumbnail in the Changelist ###
If you want to show a Thumbnail in the Changelist, you can define a Model-/Admin-Method:
```
def image_thumbnail(self):
    if self.image:
        return '<img src="%s" />' % self.image.url_thumbnail
    else:
        return ""
image_thumbnail.allow_tags = True
```