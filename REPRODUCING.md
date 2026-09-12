# Reproduction Instructions for Data Package

This data package is designed for standalone analysis reproduction using either Python or R.

## Standalone Python Replay

```bash
# Clone or download this repository
git clone https://github.com/Rohil72/historical-memory-equity-data.git
cd historical-memory-equity-data

# Using the Core-RL-Agent reproduction script:
python -m memory_study.reproduce_release --bundle . --output ./validation/replay_output
python -m memory_study.validate_release --bundle . --replay ./validation/replay_output
```
