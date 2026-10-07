## [0.4.3] - 2026-10-07

### Added
- **Camera & Motion Sensor FOV Coverage in Design Mode**:
  - Rendered directional Field of View (FOV) coverage geometry on the canvas for visual security auditing.
  - Indigo-tinted coverage cones (`#818cf8`) and directional line vectors with arrowheads for camera endpoints.
  - Emerald green PIR coverage arcs (`#34d399`) and directional line vectors for motion sensors.
  - Live FOV depth and beam angle adjustments via the Endpoint Properties panel.
- **Architectural Room Dragging & Movement**:
  - Added draggable bounding border (`.room-drag-border`) allowing architectural rooms and sub-areas to be freely moved across the floor plan.
- **Context Menu Actions**:
  - Expanded right-click context menu capabilities: Duplicate Room/SubArea, Change Style / Color, View Properties, Rotate (±90°, 180°), and Delete.
- **Keyboard Element Deletion**:
  - Supported `Delete` and `Backspace` keys for immediately removing selected endpoints, rooms, and sub-areas with undo support and autosave.
- **Application Version Display**:
  - Integrated `__APP_VERSION__` badge (`v0.4.3`) in the top brand header for instant version visibility.
  - Added dedicated version pill inside the Settings modal header.
- **Design Enhancements Playwright E2E Suite**:
  - Added `frontend/e2e/design-enhancements.spec.ts` covering FOV coverage cones, version badges, keyboard deletion, room resizing, and context menu actions.

### Fixed
- **SVG Endpoint Hitbox & Layer Collision**:
  - Encapsulated endpoint hitboxes within dedicated `<rect class="endpoint-hitbox">` elements, resolving event fallthrough to underlying room geometry during multi-selection.
- **Toolbar & Minimized Pill Clearance**:
  - Adjusted minimized entity and property pill offsets to `top: 120px` to eliminate click collisions with top toolbar preset buttons.
- **Room Resizing Handle Cursor Count**:
  - Moved room drag cursor styling into `.room-drag-border` class to preserve exact 8-handle resize target detection.
