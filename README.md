# MySQL Examples
`meta` column contains JSON array, find were `meta.formID` matches<br>
*(Used for searching JSON data)*
```sql
SELECT * FROM wp_gf_addon_feed WHERE meta->>"$.formID" = 'f5197b84-7f74-4545-b4a7-128e4fb382c1'
```
`meta_value` column contains JSON array, only retrieve `meta_value.users` object/array from JSON<br>
*(Used for searching JSON data)*
```sql
SELECT JSON_QUERY(meta_value, '$.users') AS users FROM wp_postmeta WHERE meta_key = '_facility_meta'
```
`meta_value` column contains JSON array, only retrieve `meta_value.address` from JSON<br>
*(Used for searching JSON data)*
```sql
SELECT JSON_VALUE(meta_value, '$.address') AS address FROM wp_postmeta WHERE meta_key = '_facility_meta'
```

---

# CLI Examples
Find all `.avi` files in folder and convert to `.mp4` using FFMPEG<br>
*(New file labelled using input, starting at second character and stopping after two total characters plus **E** at beginning)*
```console
for i in *.avi; do ffmpeg -i "$i" "E${i:1:2}.mp4"; done
```
Find all `.mp4` files in folder and get their duration in seconds using FFPROBE, add filename and duration to `CSV`
```console
for i in **/*.mp4; do eval $(ffprobe -v quiet -show_format -of flat=s=_ -show_entries stream=duration $i); echo $i,$streams_stream_0_duration >> ~/Downloads/videos.csv; done;
```
Run [clean-html](https://www.npmjs.com/package/clean-html "HTML cleaner and beautifier") on all `.html` files within current directory and subdirectories
```console
find . -type f -name "*.html" -exec clean-html "{}" --in-place \;
```
Move multiple file type within current directory and subdirectories to target directory
```console
find . -type f \( -name \*.jpeg -o -name \*.jpg -o -name \*.png -o -name \*.svg -o -name \*.gif \) -exec mv "{}" ~/targetDir \;
```
Find all `.png` within current directory and subdirectories and optimize with `optipng`
```console
for img in $( find . -type f -iname "*.png" ); do optipng $img -out ${img%.*}.png; done;
```
Find all `.jpg` within current directory and subdirectories and optimize with `jpegoptim` with 80% quality
```console
for img in $( find . -type f -iname "*.jpg" ); do jpegoptim -m 80 ${img%.*}.jpg; done;
```
