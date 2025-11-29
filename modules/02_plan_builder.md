### **Module 2 — Plan Builder (Options → Days)**

# Change log
- 2025-11-28: Refined plan_builder.md based on AI critique — added proximity thresholds, budget enforcement, theme tags, weather backups, and conflict detection.

Create a short list of candidate activities (e.g., attractions, restaurants, parks). Each activity includes:
- type (theme tag: museum, food, outdoor, shopping, etc.)
- estimated duration
- cost range
- distance from lodging or fallback anchor (city center if lodging missing)
- indoor/outdoor flag for weather awareness

Day-building loop
for each day:
- Initialize anchors and constraints
  - Use lodging location; if missing, fallback to city center.
  - Track daily budget and remaining time windows.
  - Add buffers for travel (15–30 min).

- Morning activity (near lodging)
  - Distance ≤ 2–4 km or ≤ 25 min travel.
  - Duration ≤ 2–3h.
  - Prefer indoor if poor weather.
  - Select highest-scoring option; store backup.

- Midday activity
  - Within 10–15 min of prior activity.
  - Include meal if none yet.
  - Respect remaining budget.
  - Select highest-scoring option; store backup.

- Afternoon activity (different theme)
  - Theme ≠ prior slot.
  - Duration ≤ 2–3h.
  - Weather-aware substitution if outdoor blocked.
  - Select highest-scoring option; store backup.

- Evening restaurant or optional event
  - Match remaining budget tier.
  - Add “reservation recommended” if popular.
  - Only include event if time and availability fit.
  - Select highest-scoring option; store backup.

Conflict check
- Verify total time + transit + buffers ≤ daily bounds.
- If overflow, replace with backups or drop lowest-score item.

Output
- Present final picks with notes (cost tier, duration, distance/time).
- Include one backup per slot for weather or timing surprises.

Notes
- Budget enforcement: Sum activity costs; reject or adjust if daily cap is exceeded
- Theme diversity: Prevent same theme back-to-back unless user preference overrides.
- Weather handling: Outdoor activities swapped for indoor backups when conditions poor.
