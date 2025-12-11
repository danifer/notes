ImageMagick commands for image manipulation including resize, add borders, convert formats, and aspect ratio adjustments.

---

Convert a 1024x1024 image into a 4x6 picture with white borders at the top and bottom
    magick source_image.png -resize 1024x1024 -background white -gravity center -extent 1024x1536 +repage target_image.jpg
