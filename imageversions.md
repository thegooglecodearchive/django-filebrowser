# Using Image Versions #

With the **FileBrowser**, you are able to define different versions/sizes for Images. This enables you to save an Original Image on your Server while having different versions of that Image to automatically fit your websites Grid.

## How to use it ##

  * **The Grid**
> > First you need to know which versions/sizes of an Image you´d like to use on your Website. Let´s say you´re having the following Grid for your Website:
    * **12 Columns with 60px for each column and 20px margin. (which is a total of 940px).**

  * **Image Versions/Sizes**
> > With this Grid, you could (for example) save these Image Versions:
    * **Thumbnail**: 140px (2 Columns).
    * **Small**: 300px (4 Columns); for Overview-Pages.
    * **Medium**: 460px (6 Columns).
    * **Big**: 620px (8 Columns).
    * **Cropped**: 60px/60px (1 Column).
    * **Cropped Thumbnail**: 140px/140px (2 Columns).

  * **Defining Image Versions**
> > Use settings.py to define the name of your image-versions directory as well as the versions/sizes of your Images.
```
VERSIONS = getattr(settings, "FILEBROWSER_VERSIONS", {
    'thumbnail': {'verbose_name': 'Thumbnail (140px)', 'width': 140, 'height': '', 'opts': ''},
    'small': {'verbose_name': 'Small (300px)', 'width': 300, 'height': '', 'opts': ''},
    'medium': {'verbose_name': 'Medium (460px)', 'width': 460, 'height': '', 'opts': ''},
    'big': {'verbose_name': 'Big (620px)', 'width': 620, 'height': '', 'opts': ''},
    'cropped': {'verbose_name': 'Cropped (60x60px)', 'width': 60, 'height': 60, 'opts': 'crop'},
    'croppedthumbnail': {'verbose_name': 'Cropped Thumbnail (140x140px)', 'width': 140, 'height': 140, 'opts': 'crop'},
})
```
  * When browsing a folder, you see the Icon for Image-Versions on the left-hand side of each row. Clicking that Icon, you´ll see the different Versions available for an Image.


## Accessing Image-Versions in a Template ##

See [Templatetags](templatetags.md).