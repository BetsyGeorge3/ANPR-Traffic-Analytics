# UAE ANPR & Traffic Analytics: Scope

## Goal
A deployed, demo-able portfolio prototype that detects vehicles, reads UAE
license plates, and produces basic traffic analytics from video and images.
Not a production system.

## Inputs
- Images (JPG/PNG)
- Video files (MP4), 720p–1080p, fixed camera

## Outputs
- Plate text, validated against UAE format rules
- Emirate (+ plate code where present)
- Vehicle class (car, truck, bus, motorcycle)
- Counts per direction and class (virtual line)
- Dwell time / occupancy per zone
- Approximate speed (homography, uncalibrated, labeled as approximate)
- Results stored in SQLite/Postgres, exposed via API + dashboard

## Out of scope
- Real-time multi-camera streaming at scale
- Automatic enforcement / fines
- Identifying individuals
- Publishing footage with readable plates

## Success metrics (targets, to be measured honestly)
| Metric | Target |
|---|---|
| Plate detector mAP@50 | ≥ 0.90 on held-out test scenes |
| Full-plate exact-match accuracy | Report as measured, by condition (day/night/angle) |
| Character-level accuracy | Report as measured |
| Tracking | Stable ID across the vehicle's pass (ID switches counted) |
| Latency | FPS before/after ONNX export |

## Data rules
- Only footage/images I have the right to use; log license of every dataset
- Split train/val/test by scene or video, never by frame
- Test set size and variety documented in the README

## Privacy
- Plate masking/hashing in stored logs, retention policy, PDPL note (Day 28)

## Deliverables
Repo + README with metrics and failure cases, FastAPI service, Streamlit
dashboard, Docker image, cloud demo (or recorded demo), 2-min pitch.
