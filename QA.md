# Responsive and gameplay QA

## Corrected behavior

- Removed the viewport minimum height that cropped short embeds.
- Measured the actual game container instead of assuming the browser window size.
- Reserved the real header and footer areas when spawning and moving targets.
- Repositioned targets after resize and rotation, with fewer targets when space is limited.
- Kept menu and results screens scrollable on small displays.
- Made fullscreen accessible from the title screen and requested it on Clock In.
- Preserved playability when fullscreen is unavailable or blocked by an embed.
- Added browser viewport resize handling and supported display safe areas.
- Removed the fixed keyboard aiming limits.
- Cleared held input on pause, focus loss, visibility changes, and game over.
- Isolated the active spray pointer from additional touches.
- Preserved native keyboard activation of buttons.
- Made spray cadence consistent across tested frame rates.
- Ignored invalid saved high scores.

## Verification

Automated browser checks passed in **Microsoft Edge (Chromium), headless mode**.

| Viewport | Checks |
| --- | --- |
| 240 × 240 | Reachable start button, visible controls, bounded targets |
| 280 × 320 | Small menu and retry screen |
| 320 × 240 | Short embed |
| 320 × 568 | Small portrait layout |
| 390 × 844 | Portrait phone layout |
| 540 × 720 | Narrow layout breakpoint |
| 640 × 360 | Small landscape layout |
| 844 × 390 | Landscape phone layout |
| 1024 × 768 | Tablet-sized layout |
| 1440 × 900 | Desktop layout |
| 2560 × 1080 | Wide display |
| 3840 × 2160 | 4K display |

Across these sizes: no document horizontal overflow, clipped action buttons, or target centers placed outside the playable area. Target radii were also checked against the reserved play area.

Additional checks passed for fullscreen entry/exit, blocked fullscreen fallback, live portrait-landscape resize, pause timer, open-eye damage, closed-eye immunity, scoring, refill, pointer release/cancellation, second-pointer isolation, keyboard controls, focus-loss pause, victory, defeat, and retry. Spray consumption remained within one spray pulse across 15/30/60/120 FPS simulations. The shipping build loaded without JavaScript errors.

## Test boundaries

Phone layouts and touch events were emulated; this is not a physical-device certification. Safari/iOS, Firefox, and the final live itch.io embed were not tested. Fullscreen availability depends on browser support and iframe permissions. For itch.io, select **Click to launch in fullscreen**, upload the updated ZIP, and preview the published embed.
