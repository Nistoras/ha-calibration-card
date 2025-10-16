# =============================
# README — What you'll get
# =============================
# This package gives you a reusable "Calibration Card" workflow in Home Assistant
# to compute and persist surface calibration constants (k, w) per location, with:
# • Two modes: Laser (IR) or Preset (surface type)
# • Entity-or-Manual inputs for Ti/Te/RH/T_stick/T_IR
# • EMA persistence (lambda) so new calibrations blend with older ones
# • JSON store with history per location (last 20 entries)
# • Example Lovelace dashboard (no custom cards needed)
#
# You DON'T need Git experience; just follow the steps below.
#
# =============================
# 0) Prerequisites
# =============================
# • Home Assistant 2024.6 or newer.
# • Basic access to File Editor / config folder.
# • Optional: an IR thermometer; optional: real sensor entities for temp/RH.
#
# =============================
# 1) Enable "packages" (one-time)
# =============================
# In configuration.yaml add (or merge) the following and restart HA once:
#
# homeassistant:
# packages: !include_dir_named packages
#
# Create a folder /config/packages if it does not exist.
#
# =============================
# 2) Create file: /config/packages/calibration_package.yaml
# =============================


# --------------------------------------------------
# OPTIONAL: Lovelace Dashboard View (copy into a YAML-mode view)
# --------------------------------------------------
# Create a new dashboard (Settings → Dashboards → + Add → YAML mode),
# point it to /config/dashboards/calibration-dashboard.yaml and paste the section below there.


# --- FILE: /config/dashboards/calibration-dashboard.yaml ---
# Paste the content below into /config/dashboards/calibration-dashboard.yaml (uncommented)



cd /config
mkdir -p packages dashboards
git clone https://github.com/Nistoras/ha-calibration-card.git tmp_cal
cp -f tmp_cal/calibration_package.yaml packages/
cp -f tmp_cal/calibration-dashboard.yaml dashboards/
rm -rf tmp_cal
ha core restart
