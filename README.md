# blurry-clean
clean SLiM theme with a blurred out background

install:

* copy the blurry-clean folder to /usr/share/slim/themes
* open /etc/slim.conf and insert `current_theme  blurry-clean`

intended to work with [wpgtk](https://github.com/deviantfero/wpgtk) and this [script](https://github.com/roqstr/dotfiles/blob/master/script/themechg.py)

relevant snippet:
```
walldir = "/home/marco/.wallpapers/"
slimbg = "/usr/share/slim/themes/blurry-clean/background.png"

files = [ elem for elem in files if not ".Xres" in elem ]
files = [ elem for elem in files if not ".sample" in elem ]
files = [ elem for elem in files if not ".colors" in elem ]
files = [ elem for elem in files if not ".current" in elem ]
files = [ elem for elem in files if not ".sh" in elem ]

x = random.randint(0, len(files) - 1)

shutil.copy(walldir + files[x], slimbg)
im = Image.open(slimbg)
imBlurred = im.filter(ImageFilter.GaussianBlur(10.0)) 
imBlurred.save(slimbg, "PNG")
```
