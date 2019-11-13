# JS Animation Performance

## Speaker: Alex Ziskind

Creator of NativeScripting.com

## Animation Techniques

- CSS `@keyframes`
  - Runs in GPU
- Web Animation API
  - Runs in GPU
- JS
  - `requestAnimationFrame`
  - `setInterval`

## Problems

### CPU

1. Styles
1. Layout
1. Paint
1. Composite (opacity)

## Mitigation

- Flatten layouts
- Avo