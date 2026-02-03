---
inclusion: fileMatch
fileMatchPattern: "**/*.tsx,**/*.jsx,**/*.vue,**/*.svelte,**/components/**,**/pages/**,**/views/**"
triggers: ["frontend", "component", "React", "Vue", "UI", "UX", "state", "styling", "CSS"]
---

# Frontend Specialist

## Activation

This specialist activates when working on:
- UI components
- State management
- Styling and CSS
- User interactions
- Accessibility
- Frontend performance

## Analysis Checklist

### 1. Component Design
- [ ] Components have single responsibility
- [ ] Props interface clearly defined
- [ ] Default props provided where sensible
- [ ] Component is reusable (not over-specialized)
- [ ] Composition over inheritance

### 2. State Management
- [ ] State lives at appropriate level
- [ ] Derived state computed, not stored
- [ ] Side effects isolated (useEffect, watchers)
- [ ] Loading/error states handled
- [ ] Optimistic updates where appropriate

### 3. Accessibility (a11y)
- [ ] Semantic HTML elements used
- [ ] ARIA labels on interactive elements
- [ ] Keyboard navigation works
- [ ] Color contrast sufficient (WCAG AA)
- [ ] Focus management correct
- [ ] Screen reader tested

### 4. Performance
- [ ] Large lists virtualized
- [ ] Images lazy loaded
- [ ] Bundle size reasonable
- [ ] Memoization used appropriately
- [ ] No unnecessary re-renders

### 5. User Experience
- [ ] Loading states provide feedback
- [ ] Error messages are helpful
- [ ] Forms validate on blur/submit
- [ ] Responsive design works
- [ ] Animations don't block interaction

## Common Issues to Flag

| Issue | Severity | Recommendation |
|-------|----------|----------------|
| Missing alt text on images | 🟠 High | Add descriptive alt text |
| No loading state | 🟡 Medium | Add skeleton/spinner |
| Inline styles | 🟢 Low | Move to CSS/styled components |
| Missing error boundary | 🟡 Medium | Add error boundary |
| No keyboard support | 🟠 High | Add keyboard handlers |
| Prop drilling > 3 levels | 🟡 Medium | Consider context/state management |

## Questions to Ask

1. **Users**: Who uses this? Desktop/mobile/both?
2. **Accessibility**: WCAG level required (A, AA, AAA)?
3. **Browser Support**: Which browsers/versions?
4. **Performance**: Target load time? Core Web Vitals?
5. **Offline**: Offline support needed?
