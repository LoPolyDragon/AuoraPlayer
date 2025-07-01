Create a comprehensive JSON design system profile by analyzing the provided screenshots. Extract all visual design patterns, component structures, and styling conventions that would enable Cursor AI to consistently replicate this design language across new implementations.
Specific Requirements:
Element-Specific Color Mapping: For each visual element, specify EXACTLY where colors are applied:
Card backgrounds vs card borders vs card content
Button backgrounds vs button text vs button icons
Icon fills vs icon containers vs icon backgrounds
Text colors for different hierarchy levels
Background gradients and their precise application areas
Accurate Color Extraction: Provide precise hex values by analyzing:
Gradient start/end colors and their direction
Shadow colors and opacity values
Hover state color variations
Border colors vs fill colors
Text color contrast ratios
Context-Aware Styling Rules: Document styling with specific application context:
"Card containers have gradient X, but card icons use solid color Y"
"Primary buttons use gradient A on background, secondary buttons use color B"
"Navigation icons are color C, but action icons are color D"
Visual Effect Placement: Specify exactly which elements receive visual treatments:
Which elements have shadows (and shadow specifications)
Which elements have gradients (and gradient specifications)
Which elements have border radius (and specific radius values)
Which elements have hover animations
Component State Mapping: For each component, document:
Default state styling
Hover state changes (what changes and how)
Active/pressed state appearance
Disabled state styling
Focus state indicators
Output Format: Structure as a detailed JSON object that maps styling to specific elements:

json
{
  "elementStyling": {
    "cards": {
      "background": "linear-gradient(135deg, #FF6B6B 0%, #4ECDC4 100%)",
      "border": "#E0E0E0",
      "shadow": "0 4px 12px rgba(0,0,0,0.1)",
      "icons": {
        "fill": "#FFFFFF",
        "background": "none"
      }
    },
    "buttons": {
      "primary": {
        "background": "#007AFF",
        "text": "#FFFFFF",
        "hover": {
          "background": "#0056CC"
        }
      }
    }
  }
}


Include specific selectors/contexts for each styling rule.
Content Exclusion: Focus purely on design structure and visual patterns - ignore specific text content, actual images, or branded elements.
AI Replication Goal: The JSON should serve as a precise style guide that prevents styling misplacement. Each visual effect should be mapped to its exact element context so Cursor AI applies:
Gradients to the correct elements (cards vs icons vs buttons)
Colors to the right component parts (backgrounds vs text vs borders)
Visual effects to appropriate contexts (shadows on containers, not content)
Color Accuracy Techniques:
Sample colors from multiple points on gradients
Note gradient directions (linear, radial, angle)
Distinguish between overlay colors and base colors
Account for transparency/opacity in layered elements
Specify color variations for different states
Critical: Include "DO NOT" rules to prevent common misapplications like putting card gradients on icons or button colors on text elements.
Provide actionable, specific data that translates directly into code implementation.
