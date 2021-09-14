# MySQL Examples
`meta` column contains JSON array, find were `meta.formID` matches
*(Used for searching JSON data)*
```sql
SELECT * FROM wp_gf_addon_feed WHERE meta->>"$.formID" = 'f5197b84-7f74-4545-b4a7-128e4fb382c1'
```

# CLI Examples
Find all `.avi` files in folder and convert to `.mp4` using FFMPEG
*(New file labelled using input second through third characters plus **E** at beginning)*
```console
for i in *.avi; do ffmpeg -i "$i" "E${i:1:2}.mp4"; done
```
