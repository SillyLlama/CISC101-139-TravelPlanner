### **Module 2 — Plan Builder (Options → Days)**

# Change log
- 2025-11-28: Refined plan_builder.md based on AI critique — added proximity thresholds, budget enforcement, theme tags, weather backups, and conflict detection.

# Change log
2025-11-28: Refined plan_builder.md based on AI critique — added proximity thresholds, budget enforcement, theme tags, weather backups, and conflict detection.

## Building Activity List
Create a short list of candidate activities (e.g., attractions, restaurants, parks). Each activity includes:
- type (theme tag: museum, food, outdoor, shopping, etc.)
- estimated duration
- cost range
- distance from lodging or fallback anchor (city center if lodging missing)
- indoor/outdoor flag for weather awareness

## Day-building loop for each day
### Limits and constraints
- Use lodging location; if missing, fallback to city center  
- Track daily budget and remaining time windows  
- Add buffers for travel (15–30 min)  

### Morning activity
- Distance ≤ 2–4 km or ≤ 25 min travel  
- Duration ≤ 2–3h  
- Prefer indoor if poor weather  
- Select the highest-scoring option  

### Midday activity
- Within 10–15 min of prior activity  
- Include meal if none yet  
- Respect remaining budget  
- Select the highest-scoring option  

### Afternoon activity (different theme)
- Theme ≠ prior slot  
- Duration ≤ 2–3h  
- Weather-aware substitution if outdoor blocked  
- Select the highest-scoring option  

### Evening restaurant or optional event
- Match remaining budget tier  
- Add “reservation recommended” if popular  
- Only include event if time and availability fit  
- Select the highest-scoring option  

## Conflict check
- Verify total time + transit + buffers ≤ daily bounds  
- If overflow, replace with backups or drop lowest-score item  

## Output
- Present final picks with notes (cost tier, duration, distance/time)  
- Include one backup per slot for weather or timing surprises  

## Notes
- Add up estimated activity costs and adjust or replace options if they push the day over budget  
- Avoid scheduling the same type of activity twice in a row unless the user specifically prefers it  
- If the weather is poor, replace outdoor activities with suitable indoor backups  
- When lodging isn’t provided, use a central city location to estimate distances  
- If information is missing (e.g., cost or duration), make reasonable estimates and flag them with a short confidence note  
