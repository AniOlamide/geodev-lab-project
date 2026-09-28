1. My Question (1 sentence)
How much area is within 500m walking distance of health facilities in Lagos State, to identify service coverage gaps?
2. Operation I Ran and Why
Operation:Buffer
Translation:Health Facilities within 500 metres of another= Buffer, 
Input:Lagos_Health — extracted_loca` (points) and `LAG LGAS` (boundary) from `data/processed/`
Tool:Vector > Geoprocessing Tools > Buffer
Distance:500 metres
CRS:Reprojected to WGS 84 / UTM Zone 31N (EPSG:32631) - so distance is in metres, not degrees. My QGIS project was set to EPSG:32631.
Output:data/processed/LSHF_Buffer_500m.gpkg` + map `maps/week4_LSHF_Buffer.png`
3. What I Expected vs What I Got
Expected:I expected 500m buffers around 320 health facilities, mostly clustered in Ikeja, Lagos Island, and Surulere. I expected some overlap in urban LGAs.
Got:I got buffer polygons. Attribute table shows 320<img width="816" height="1056" alt="week4_LSHF_buffers png" src="https://github.com/user-attachments/assets/7c489759-ecee-40de-8d94-a6f703f0115c" />
 rows - matches expected. Visually, buffers are heavily overlapping in Lagos Island/Ikeja, and sparse in Badagry and Epe LGAs.
4 Checks:
    1. Map view: Yes, buffers are around health points, inside Lagos State boundary.
    2. Attribute table: 320 features - matches input points.
    3. Hand check: I picked 1 facility in Alimosho, measured distance to edge of its buffer with Measure Tool - ~500m.
    4. Empty geometry: No null geometries found.

4. What Surprised Me
 The overlap is extreme in central Lagos - if I used Dissolve, it becomes almost one big polygon. I did NOT dissolve so I can count later.
 Some coastal facilities buffer extends into water - I need to clip with LGA boundary later. 
 My first layout export was blank because I forgot to Add Map item and drag rectangle. Fixed by adding Map in Print Layout.

 5. What Data I Still Need
 Population data per LGA to calculate how many people live outside 500m buffer (to show underserved areas).
 Road network to do a more accurate network buffer, not just circular.
 LGA boundary with accurate 2024 population for spatial join count.

<img width="816" height="1056" alt="week4_LSHF_buffers png" src="https://github.com/user-attachments/assets/46efe21f-9829-41fa-89b6-68430e634ccd" />
 6. Map
