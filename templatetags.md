# Templatetags #
New in Version 3.0: Instead of Generating Image-Versions on Upload, the Versions are now generated "on the fly" with using Templatetags.

First you need to load the templatetags with
```
{% load fb_versions %}
```

You have two different tags to choose from: **version** and **version\_object**.

### version ###
Get the URL for a version of an existing Image according to the predefined VERSIONS settings (see fb\_settings).
```
{% version field_name version_prefix %}
```
Given our Publication-Model form abeove, use
```
{% version publication.image.path 'medium' %}
```
in order to display the URL to your medium-size version.

Note: version\_prefix can either be a string or a variable. If version\_prefix is a string, use quotes.
### version\_object ###
Sometimes getting the URL to your version may not be enough. In this case, use version\_object in order to return a FileObject.
```
{% version_object field_name version_prefix as variable %}
```
With our Publication-Model, use
```
{% version_object my_image 'medium' as version_medium %} 
```
in order to retrieve the FileObject for the medium version.

With the FileObject in your Template-Context you can now type (for example):
```
{{ version_medium.width }}
```
or just
```
<img src="{{ version_medium }}" />
```

A complete (and more complex) example #001:
```
{% for publication in publication_list %}
   {% ifequal publication.image.orientation 'lancscape' %}
      <p><img src="{{ version publication.image 'medium' }}" /></p>
   {% else %}
      <p><img src="{{ version publication.image 'medium_portrait' }}" /></p>
   {% endifequal %}
{% endfor %}
```

### Behind the Scenes ###
With either using the version-tag or the version\_object-tag, the Image-version will be generated "on the fly" if the version doesn´t already exist OR if the original Image is newer than the version.
This means that if you´d like to update an Image, you just overwrite the original Image - the versions will be re-generated automatically (as you request them within your template).