## Dependencies

```
nginx
ffmpeg
inotify-tools
screen
```

Inside of your nginx config, (located at ```/etc/nginx/sites-enabled/default```)

Add the following to your "**server**" block:
```
location /images {
autoindex on;
}
```

This will allow the javascript to access all image filenames.

## Setup

Create a directory named "**content**" inside the website directory.

Within the "**content**" directory, create another named "**thumbnails**".

Edit the variables in the **compress.sh** and **dirwatch.sh** to where those two directories are.

```
input_directory="<directory of content>"
output_directory="<directory of thumbnails>"
```

Add images you want to host and display into the **content** directory.

Run **compress.sh**. This will use ffmpeg to resize and compress any images in that directory, and place the output (*of the same filenames*) into the thumbnail directory.

```sh compress.sh```

I recommend screening the **dirwatch.sh** to have it run in the background. 

```screen sh dirwatch.sh```

Now, any images you add into the **content** directory will automatically be resized, compressed, and added to the **thumbnail** directory.
