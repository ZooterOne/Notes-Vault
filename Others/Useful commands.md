## Image

```
magick <source> -resize <percent>% <destination>
```

resize an image.

```
ffmpeg -i <input>.mp4 -vf "scale=iw/2:-1:flags=lanczos" -r 15 <output>.gif
```

transform a video to an animated gif image, reducing the image size to half (iw/<n> means width will be 1/<n> of the original width, -1 refers to the height and is calculated automatically) and using a framerate of 15 frames per second.

```
ffmpeg -i <input>.mp4 -vf fps=1/10 snapshot%03d.png
```

generate snapshots of a video at every 10 seconds.

___

## Virtual box

```
sudo mount -t vboxsf -o uid=1000,gid=1000 <share name> <folder>
```

Enable a shared folder from a virtual machine.

___

## File properties

```
pdfinfo <file>
```

display pdf properties.

```
exiftool <file>
```

display exif properties.