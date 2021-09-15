# MySQL Examples
`meta` column contains JSON array, find were `meta.formID` matches<br>
*(Used for searching JSON data)*
```sql
SELECT * FROM wp_gf_addon_feed WHERE meta->>"$.formID" = 'f5197b84-7f74-4545-b4a7-128e4fb382c1'
```
`meta` column contains JSON array, only retrieve `meta.formID` from JSON<br>
*(Used for searching JSON data)*
```sql
SELECT meta->>"$.formID" FROM wp_gf_addon_feed
```

---

# CLI Examples
Find all `.avi` files in folder and convert to `.mp4` using FFMPEG<br>
*(New file labelled using input, starting at second character and stopping after two total characters plus **E** at beginning)*
```console
for i in *.avi; do ffmpeg -i "$i" "E${i:1:2}.mp4"; done
```
