# CustomNovaX Theme - Changelog

## Version 1.0 - Initial Release (2026-01-31)

### Overview
CustomNovaX is an independent, customized variation of the Nova X theme for Playnite Desktop. Created to maintain update-safe modifications without affecting the original Nova X theme.

### Major Changes

#### Details View (DetailsViewGameOverview.xaml)

**1. Description Tab** (NEW)
- Moved game description to dedicated tab with proper styling
- Original element hidden with `Visibility="Collapsed"`
- Full HTML support for rich text descriptions
- Applied Grid layout with MaxWidth constraint to prevent full-width expansion

**2. Steam Reviews Tab** (NEW)
- Extracted ReviewViewer plugin control to dedicated tab
- Applied Grid layout matching main Game Details style
- Visibility controlled by ReviewViewer plugin status
- Properly constrained with MaxWidth for consistent layout

**3. Related Games Tab** (NEW)
- Integrated GameRelations plugin with four expandable categories:
  - Similar Games
  - Same Series  
  - Same Developer
  - Same Publisher
- Visibility proxy system ensures tab only shows when data available
- Grid layout with MaxWidth constraint

**4. Activity Tab** (NEW)
- Dedicated tab for GameActivity plugin data visualization
- Displays time-based activity charts
- Grid layout with MaxWidth constraint
- Visibility bound to plugin data availability

#### Grid View (GridViewGameOverview.xaml)

**HowLongToBeat Repositioning** (MODIFIED)
- Moved HLTB section from mid-position to Grid.Row="0" (very top)
- Now displays before Game Details section in grid view overlay
- Added bottom margin (`Margin="0,0,5,15"`) to prevent overlap
- Maintains all plugin bindings and data templates

### Technical Implementation

**Tab Order in Details View:**
1. Game Details (original core content)
2. Description (NEW - game description)
3. Steam Reviews (NEW - reviews from plugin)
4. Related Games (NEW - game relations plugin)
5. Activity (NEW - activity tracking plugin)
6. WebExplorer (original - web browser integration)

**Layout Approach:**
- All new tabs use `Grid Margin="0,32,0,0" MaxWidth="{DynamicResource DetailsViewDetailsMaxWidth}"`
- Matches main Game Details tab styling for visual consistency
- Prevents full-width expansion to maintain compact layout
- DetailsPanelRoundedBorder style applied to content containers

**Styling Details:**
- Border radius: 3px (DetailsPanelRoundedBorder)
- Padding: 20,14,20,14
- Margin: 0,0,0,32 (bottom spacing between sections)
- Font sizing uses DynamicResource for theme consistency

### Plugin Dependencies

| Plugin | Tab | Optional | Function |
|--------|-----|----------|----------|
| ReviewViewer | Steam Reviews | Yes | Displays user/critic reviews from various sources |
| GameRelations | Related Games | Yes | Shows similar games, series, developer, publisher |
| GameActivity | Activity | Yes | Displays time-based activity charts |
| HowLongToBeat | (repositioned) | Yes | Game completion time estimates |

All plugins are optional. Tabs hide automatically if plugin not installed or no data available.

### Files Modified

- **Views/DetailsViewGameOverview.xaml**
  - Added 4 new TabItems with Grid layout
  - Hidden original Description element
  - Total additions: ~200 lines of XAML

- **Views/GridViewGameOverview.xaml**
  - Moved HowLongToBeat Expander to Grid.Row="0"
  - Added 15px bottom margin for spacing
  - Total changes: 1 repositioning + 1 margin adjustment

- **theme.yaml**
  - ID: CustomNovaX (unique identifier)
  - Name: Custom Nova X
  - Author: Alberto
  - Version: 1.0
  - ThemeApiVersion: 2.8.0

### Installation & Setup

**Prerequisites:**
- Playnite Desktop v10.49.0+
- Nova X theme base (recommended but customizations are independent)

**Installation Steps:**
1. Navigate to `C:\Users\[YourUsername]\AppData\Local\Playnite\Themes\Desktop\`
2. Extract CustomNovaX folder
3. Launch Playnite
4. Settings > Appearance > Theme dropdown
5. Select "Custom Nova X"
6. Click Apply
7. Restart Playnite (recommended)

**Verification:**
- Game details view should show new tabs: Description, Steam Reviews, Related Games, Activity
- Grid view overlay should show HowLongToBeat at top with spacing from other details
- All original functionality preserved

### Compatibility Matrix

| Feature | Status | Notes |
|---------|--------|-------|
| Desktop Mode | ✅ Supported | Fully tested and working |
| Fullscreen Mode | ⚠️ Unknown | Not yet tested |
| Plugin System | ✅ Supported | All original plugins work |
| Theme Inheritance | ✅ Supported | Inherits from Nova X base |
| Updates | ✅ Protected | Independent from Nova X updates |

### Performance Notes
- Tab loading is lazy - content loads only when tab selected
- No performance degradation from additional tabs
- All bindings remain reactive and responsive

### Known Limitations
1. Description HTML rendering depends on HtmlTextView control capabilities
2. Related Games tab visibility requires GameRelations plugin installed
3. Activity data requires game playtime data in Playnite

### Future Enhancement Ideas
- Custom color palette variations
- Alternative layout templates
- Additional plugin integrations
- Fullscreen mode customizations
- Draggable/customizable tab order

### Support & Maintenance
- This theme is independent from Nova X
- Updates to Nova X will NOT affect CustomNovaX
- All customizations persist through Playnite updates
- Safe to use with other theme modifications

---

**Theme Metadata:**
- ID: CustomNovaX
- API Version: 2.8.0
- Base Theme: Nova_X (v1.27)
- Base Theme Author: darklinkpower
- Author: Alberto
- Release Date: 2026-01-31
- Status: Stable (v1.0)

**Last Updated**: [Current Date]  
**Created By**: Alberto  
**Based On**: Nova_X v1.27 - https://github.com/darklinkpower/Nova-X
