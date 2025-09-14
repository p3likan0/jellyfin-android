# Quest 3 Controller Support for Jellyfin Android

This document outlines the Quest 3 controller button mappings added to the Jellyfin Android app for VR media playback control.

## Controller Button Mappings

| Quest 3 Controller Button | Action | Alternative Buttons |
|---------------------------|--------|-------------------|
| **A Button** (Right controller) | Play/Pause | X Button, Enter, Space, D-pad Center |
| **X Button** (Left controller) | Play/Pause | A Button, Enter, Space, D-pad Center |
| **Right Trigger (R1/R2)** | Fast Forward | D-pad Right |
| **Left Trigger (L1/L2)** | Rewind | D-pad Left |
| **D-pad Up** | Previous Chapter | - |
| **D-pad Down** | Next Chapter | - |
| **D-pad Left** | Rewind | Left Triggers |
| **D-pad Right** | Fast Forward | Right Triggers |
| **Y Button** | Toggle Controls Visibility | Menu Button |
| **B Button** | Back (system handled) | Back Button |

## Media Key Support

The app also supports standard Android media keys:
- `MEDIA_PLAY_PAUSE` - Toggle play/pause
- `MEDIA_PLAY` - Play
- `MEDIA_PAUSE` - Pause
- `MEDIA_NEXT` - Next episode/item
- `MEDIA_PREVIOUS` - Previous episode/item
- `MEDIA_FAST_FORWARD` - Fast forward
- `MEDIA_REWIND` - Rewind

## Implementation Details

### Files Modified:
1. **AndroidManifest.xml**: Added gamepad and touchscreen hardware features (optional)
2. **PlayerFragment.kt**: Added controller input handling with key event listeners
3. **MainActivity.kt**: Added fallback key event handling

### Key Features:
- **Focus Management**: PlayerView is set to be focusable to receive key events
- **Event Filtering**: Only KEY_DOWN events are processed to avoid duplicate actions
- **Graceful Fallbacks**: Multiple button mappings for the same action
- **State Awareness**: Play/pause respects current player state
- **Controller Visibility**: Option to toggle media controls with Y button

## Usage Instructions

1. Install the app on your Quest 3 device
2. Connect your Quest 3 controllers 
3. Open the Jellyfin app and start playing media
4. Use the controller buttons as mapped above to control playback

## Technical Notes

- The implementation uses Android's standard KeyEvent system
- Controller input is handled at both Fragment and Activity levels for robustness
- The app declares optional gamepad support in the manifest for better VR store compatibility
- All existing gesture and touch controls remain fully functional
