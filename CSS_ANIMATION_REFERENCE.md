# Hero Section CSS - Animation Reference

## New Animation Classes

### `.slide-bg`
**What**: Background image element
**New features**:
- Initial scale: 1.12 (zoom in effect)
- Active state scale: 1.0 (settles)
- Transition duration: 8s (cinematic slowness)
- Filter effects: brightness, contrast, saturation adjustments
- Performance: `will-change: transform` for GPU acceleration

### `.slide-tag` 
**Timing**: Appears at 200ms
```css
opacity: 0 → 1
transform: translateY(20px) → translateY(0)
duration: 800ms
easing: cubic-bezier(.34,.1,.68,1)
```

### `.slide-h1`
**Timing**: Appears at 350ms
```css
opacity: 0 → 1
transform: translateY(32px) → translateY(0)
duration: 900ms
easing: cubic-bezier(.34,.1,.68,1)
text-shadow: 0 4px 20px rgba(0,0,0,.4)
```

### `.slide-p`
**Timing**: Appears at 500ms
```css
opacity: 0 → 1
transform: translateY(20px) → translateY(0)
duration: 800ms
easing: cubic-bezier(.34,.1,.68,1)
```

### `.slide-btns`
**Timing**: Appears at 650ms
```css
opacity: 0 → 1
transform: translateY(20px) → translateY(0)
duration: 800ms
easing: cubic-bezier(.34,.1,.68,1)
```

---

## Button Animations

### `.btn-solid`
**Normal state**:
```css
background: linear-gradient(135deg, var(--gold) 0%, var(--gold2) 100%)
box-shadow: 0 4px 16px rgba(184,149,58,.3)
```

**Hover state**:
```css
background: linear-gradient(135deg, #9a7a2e 0%, #b8953a 100%)
transform: translateY(-2px)
box-shadow: 0 8px 24px rgba(184,149,58,.45)
transition-duration: 300ms
```

### `.btn-ghost`
**Normal state**:
```css
border: 2px solid rgba(255,255,255,.35)
background: rgba(255,255,255,.05)
backdrop-filter: blur(4px)
```

**Hover state**:
```css
border-color: #fff
background: rgba(255,255,255,.12)
transform: translateY(-2px)
box-shadow: 0 4px 16px rgba(255,255,255,.1)
```

---

## Progress Bar Animations

### `.slide-bar`
**Active bar fill**:
```css
@keyframes barFill {
  from { transform: scaleX(0) }
  to { transform: scaleX(1) }
}
animation: barFill 6s linear forwards;
gradient: linear-gradient(to right, var(--gold), var(--gold2))
glow: 0 0 8px rgba(184,149,58,.6)
```

---

## Navigation Arrow Animations

### `.slide-arrow`
**Normal state**:
```css
background: rgba(255,255,255,.08)
border: 2px solid rgba(255,255,255,.15)
backdrop-filter: blur(8px)
width: 52px
height: 52px
```

**Hover state**:
```css
background: rgba(255,255,255,.15)
border-color: var(--gold2)
box-shadow: 0 0 16px rgba(184,149,58,.4)
transform: translateY(-50%) scale(1.08)
transition: all 300ms cubic-bezier(.34,.1,.68,1)
```

---

## Scroll Indicator Animations

### `.scroll-indicator`
**Entry animation**:
```css
@keyframes fadeInUp {
  from { 
    opacity: 0
    transform: translateX(-50%) translateY(10px)
  }
  to { 
    opacity: 1
    transform: translateX(-50%) translateY(0)
  }
}
animation: fadeInUp 800ms ease-out 2s both
```

### `.scroll-icon::before`
**Bouncing dot**:
```css
@keyframes scrollDot {
  0% {
    opacity: 0
    transform: translateX(-50%) translateY(0)
  }
  50% { opacity: 1 }
  100% {
    opacity: 0
    transform: translateX(-50%) translateY(12px)
  }
}
animation: scrollDot 2s infinite
```

---

## Easing Functions Used

### `cubic-bezier(.34,.1,.68,1)`
- **Purpose**: Natural, slightly bouncy ease-out
- **Used for**: Text animations, smooth entries
- **Feel**: Professional, not too slow, not too fast

### `ease-out`
- **Purpose**: Standard ease-out
- **Used for**: Scroll indicator fade-in
- **Feel**: Smooth and natural

### `linear`
- **Purpose**: Constant speed
- **Used for**: Progress bar fill
- **Feel**: Predictable, steady

---

## Color Gradients

### Button gradient
```css
linear-gradient(135deg, var(--gold) 0%, var(--gold2) 100%)
```

### Progress bar fill
```css
linear-gradient(to right, var(--gold), var(--gold2))
```

### Slide overlays
- Slide 1: `linear-gradient(135deg, rgba(26,46,32,.75) 0%, rgba(26,46,32,.35) 40%, rgba(184,149,58,.08) 100%)`
- Slide 2: `linear-gradient(to right, rgba(26,20,10,.8) 0%, rgba(26,20,10,.3) 50%, rgba(26,20,10,.05) 100%)`
- Slide 3: `linear-gradient(135deg, rgba(26,26,24,.78) 0%, rgba(26,26,24,.28) 55%, transparent 100%)`

---

## Image Filters Applied

### On `.slide-bg`
```css
filter: brightness(0.75) contrast(1.08) saturate(1.15);
/* In active state: */
filter: brightness(0.85) contrast(1.15) saturate(1.2);
```

**Effect**: Enhances colors, increases contrast, makes images pop while maintaining visibility for text overlay

---

## Performance Optimizations

1. **GPU Acceleration**: `will-change: transform` on `.slide-bg`
2. **Smooth scrolling**: `scroll-behavior: smooth` on `html`
3. **Transform-based animations**: Using `transform` and `opacity` (GPU-friendly)
4. **Backdrop blur**: Hardware-accelerated filter
5. **Reduced motion support**: Can be added with `@media (prefers-reduced-motion)`

---

## Custom CSS Variables Used

```css
--gold: #b8953a       /* Primary accent */
--gold2: #d4b05a      /* Lighter gold */
--g: #1a2e20          /* Dark green */
--g2: #243d2a         /* Medium green */
--ink: #1a1a18        /* Near black */
```

---

## Responsive Adjustments

At different breakpoints, these animations maintain their cinematic feel while adapting to screen size:

- **Desktop (>1100px)**: Full animations, all elements visible
- **Tablet (768-1100px)**: Slightly reduced animation delay
- **Mobile (<640px)**: Scroll indicator hidden, arrows maintain quality
