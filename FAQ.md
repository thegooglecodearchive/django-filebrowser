This is a list of frequently asked questions. If your question is not being answered, please open a ticket.

# FAQ #

**I´ve installed the FileBrowser but it doesn´t work?**

Common errors are:
  * You´ve installed the FileBrowser to a directory which is not in your PYTHONPATH.
  * The paths are wrong: Check your projects settings-file and the FileBrowsers settings-file for all the paths. See [Available Settings](Settings.md) for more on this subject.

---

**Is the FileBrowser stable and ready for production-use?**

We are using the FileBrowser for around 20 websites right now. It´s been used by our countries largest publishing agency as well as smaller companies on a daily basis. So, the answer is **yes**.

---

**Why do I have to copy/symlink the media-directory?**

Django doesn´t serve media-files. This is done by Apache (or another webserver like lighttpd).

---

**Where should I put the media-directory?**

That depends on your server-setup. Once media-files are served correctly, you just have to change URL\_FILEBROWSER\_MEDIA in settings.py to point to the right location.
Please Note that you shouldn´t use the media-directory for your admin-files (since this might break future admin-updates).

---

**Which directory should I use as the FileBrowsers root directory?**

The FileBrowsers root directory (as defined with MEDIA\_ROOT + DIRECTOY) is a directory for files/documents on your server, which should be used by you (or your client/editors) for uploading files. Let´s say you have a directory "media" on your server which holds all your media-stuff: Within this directory you may want to put some subdirectories, e.g. "admin" (for all admin-stuff), "site" (for your websites images and css/js-files) and "uploads". In this case, "/path/to/media/" is your MEDIA\_ROOT and "uploads/" is your DIRECTORY.

---

**I've installed the FileBrowser, but I don´t see any buttons/icons?**

The path to the FileBrowser media-files is wrong. Check settings.py.

---
