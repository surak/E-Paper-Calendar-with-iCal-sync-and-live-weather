# e-Display Calendar Deployment Guide

## Overview
This Inkycal fork is configured for a Raspberry Pi e-Display (7.5" ink screen).

## Scripts

/home/pi/inky_run.py:
  - Entry point: adds /home/pi/Inkycal to path, creates Inkycal(render=True), runs inky.run()
  - Runs in infinite loop updating display every 30 minutes

/home/pi/update_calendar_config.py:
  - Interactive script to update Google Calendar private URLs
  - Updates /boot/settings.json, creates backup, requires reboot

## Cron Job
@reboot sleep 60 && python3 /home/pi/inky_run.py &
  - @reboot: runs on Pi boot
  - sleep 60: waits for network/services
  - Runs in background (&)

## Logs
/home/pi/Inkycal/logs/inkycal.log

## Key Fixes
1. 30s timeout on urlopen() in ical_parser.py
2. try/except error handling
3. Hardcoded Europe/Madrid timezone
4. Debug logging
