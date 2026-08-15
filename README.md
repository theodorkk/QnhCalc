# GA Climb QNH PWA

Small offline-capable PWA that calculates the temporary QNH used for the half missed-approach climb performance check.

## Inputs
- Aerodrome elevation (ft)
- Published missed approach level-off altitude (ft)
- Local QNH (hPa)

## Implemented method
1. Total climb = missed approach altitude - aerodrome elevation
2. Half climb = total climb / 2
3. Round upward to the next 500 ft increment
4. Apply the published table:
   - 1000 ft -> 37 hPa
   - 1500 ft -> 56 hPa
   - 2000 ft -> 74 hPa
   - 2500 ft -> 93 hPa
   - 3000 ft -> 111 hPa
   - 3500 ft -> 130 hPa
   - 4000 ft -> 148 hPa
5. Temporary QNH = local QNH - adjustment

The app refuses to extrapolate outside the published 1000–4000 ft table.

## Test example
TRD example:
- Elevation: 64 ft
- MA altitude: 4000 ft
- Local QNH: 1010 hPa

Result:
- Total climb: 3936 ft
- Half climb: 1968 ft
- Rounded half climb: 2000 ft
- Adjustment: 74 hPa
- Temporary QNH: 936 hPa

## Run locally
A service worker requires HTTP(S), not file://.

Python:
    python -m http.server 8000

Then open:
    http://localhost:8000/QNHcalc.html

## Operational note
This is a convenience calculator, not an approved performance source. Validate against current approved company documentation before operational use.
