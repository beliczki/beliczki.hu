# Pinecone Design System Analysis

## Color Palette

### Primary Colors
- **Blue Primary**: `#0000FF` or `#0051FF` - Used for primary CTAs
- **Black**: `#000000` - Text and borders
- **White**: `#FFFFFF` - Backgrounds and button fills
- **Light Gray**: `#F5F5F5` - Page background

### Text Colors
- **Primary Text**: `#000000` - Headings and body
- **Secondary Text**: `#666666` - Subtext and labels
- **Blue Accent**: `#0000FF` - Highlight words in headings

## Typography

### Headings
- **Hero H1**: 56-64px, font-weight: 700, line-height: 1.1
- **Mixed color**: Black base with blue accent words
- **Letter spacing**: -0.02em (tight)

### Body
- **Size**: 16-18px
- **Line height**: 1.6
- **Font family**: Sans-serif (Inter, system fonts)

## Button Design

### Primary Button ("Start Building")
```css
Background: #0000FF (bright blue)
Color: #FFFFFF
Padding: 14px 28px
Border-radius: 4px
Border: none
Font-weight: 600
Font-size: 16px
```

**Corner Accents**:
- Small L-shaped marks in all 4 corners
- Color: Matching button background
- Creates "focus frame" effect
- Always visible on primary buttons

### Secondary Button ("Get a Demo")

**Normal State**:
```css
Background: transparent or white
Color: #000000
Padding: 14px 28px
Border: 1px solid rgba(0,0,0,0.2)
Border-radius: 4px
Font-weight: 600
Font-size: 16px
```

**Hover State**:
```css
Border: 2px solid #000000 (intensifies)
Background: rgba(0,0,0,0.02) (subtle)
```

**Corner Accents on Hover**:
- L-shaped marks appear in corners
- Color: #000000
- Size: 8-10px lines, 1-2px thick
- Positioned 2-3px outside button border

### Corner Accent Pattern

The corner accents are small L-shaped marks that create a "targeting" or "focus" effect:

```
┌─      ─┐
│ Button │
└─      ─┘
```

**CSS Implementation**:
```css
/* Use pseudo-elements for corners */
.button::before,
.button::after,
.button-inner::before,
.button-inner::after {
    content: '';
    position: absolute;
    width: 10px;
    height: 10px;
    border-color: currentColor;
    border-style: solid;
}

/* Top-left */
.button::before {
    top: -3px;
    left: -3px;
    border-width: 2px 0 0 2px;
}

/* Top-right */
.button::after {
    top: -3px;
    right: -3px;
    border-width: 2px 2px 0 0;
}

/* Bottom-left */
.button-inner::before {
    bottom: -3px;
    left: -3px;
    border-width: 0 0 2px 2px;
}

/* Bottom-right */
.button-inner::after {
    bottom: -3px;
    right: -3px;
    border-width: 0 2px 2px 0;
}
```

## Layout Principles

1. **Generous White Space**: Clean, uncluttered layouts
2. **Precise Alignment**: Everything on a grid
3. **Button Groups**: 16px gap between buttons
4. **Corner Accents**: Visual precision markers
5. **Subtle Borders**: Thin (1px) evolving to bold (2px) on hover

## Animation & Transitions

- **Duration**: 200ms for buttons, 150ms for borders
- **Easing**: cubic-bezier(0.4, 0, 0.2, 1)
- **Corner accents**: Fade in with scale (0.8 → 1.0)
- **Border**: Thickness change (1px → 2px)

## Interactive States

### Button Hover Effects
1. Border intensifies (1px → 2px)
2. Corner accents appear (secondary only)
3. Subtle background tint
4. Maintains cursor: pointer

### Focus States
- 2px outline offset by 2px
- Uses button color
- Maintains corner accents

## Spacing System

- **xs**: 4px
- **sm**: 8px
- **md**: 16px
- **lg**: 24px
- **xl**: 32px
- **2xl**: 48px
- **3xl**: 64px

## Component Patterns

### Hero CTA Group
```html
<div class="cta-group">
    <button class="btn-primary">Start Building</button>
    <button class="btn-secondary">Get a Demo</button>
</div>
```

### Tab Navigation
- Underline style
- Selected tab: bold text + underline
- Curly braces for active state: `{agents}`
- Gray for inactive: `{rag}` `{search}`

## Brand Personality

- **Precise**: Corner accents, exact borders
- **Technical**: Engineering-focused aesthetic
- **Clean**: Minimal, functional
- **Confident**: Bold blue, clear hierarchy
- **Modern**: Contemporary sans-serif, tight spacing
