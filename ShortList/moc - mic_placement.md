
# Placement Summary Table
``` dataview
TABLE mic_title, mic_placements, mic_results_vocal_blend, mic_results_voice_instrumental_blend
FROM "projects/CLC_mic_placements" 
WHERE file.name != "Mic Placement Summary"

```

# List of Placement Notes
```dataview 
list from [[]] and !outgoing([[]]) 
```

#MOC #templated 