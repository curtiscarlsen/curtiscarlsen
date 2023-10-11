
# Placement Summary Table
``` dataview
TABLE mic_title as title, mic_test_date as tdate, mic_placements as places, mic_results_vocal_blend as voxblend, mic_results_voice_instrumental_blend as voxinst_blend
FROM "projects/CLC_mic_placements" 
WHERE file.name != "Mic Placement Summary"

```

# List of Placement Notes
```dataview 
list from [[]] and !outgoing([[]]) 
```

#MOC #templated 