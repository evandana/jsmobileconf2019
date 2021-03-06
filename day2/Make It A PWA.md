# Why Every App Should be a PWA

## Speaker: Carl Bergenhem

- PM, KendoUI Web Components
- Progress


## What is a PWA?

- **Requires** browser support for native functionality
- **Fast** Small initial Load cost
- **Integrated** Local OS look and feel
- **Reliable** Offline

There are PWA Qualifications: **Look them up**

## Why are they Important?

- 80% of time spent in 3 apps
- 87% of time spent in mobile apps
- Past the "App Gold Rush"
  - Majority of users: 0 installs / month
  - Average user: 2 installs / month
- **Easier Distribution**, without corporate (Apple, Google) bias

### Success Stories

- Starbucks saw 2x Active users and 20% mobile conversion
- Twitter Lite
- Uber
- Tinder: reduced load times from 12s to 4.69s
- West Elm: 15% increase in time spnt and 9% increase in revenue

## Why Every App Should be a PWA

### Responsive Design

- Mobile-first content (then mobile first design)
- Focus on content first
- Understand customer's actual needs (track screen size?)

#### Tools
- CSS Grid
- Flexbox
- Bootstrap

#### Responsive Images
- ~20% of a website is just images
- WebP, PNG, or JPEG (ensure compression)
- WebP
  - Save 85% file size compared to JPEG
  - Save 85% file size compared to PNG
- GIFs --> X 
  - Use .mp4 instead
- Use SVGs: `<img src="abc.svg" />`
- Font icons
  - Lazy loading fonts may cause a content refresh flash
- SVG Icons
  - Individually mutable parts
  - Accessible
  - Inline and external
- `<img />` attributes: `srcset` & `sizes` for viewport loading the right file
- `<picture><source media="" /><img /></picture>`
  - Allows you to swap images based on viewport size

## Performance

- First Paint
- First Contentful Paint
- First Meaningful Paint
- Time to Interactive
- ...

### Actions to Take

- Responsive Images
- Remove superfluous dependencies
- Avoid one large single bundle
- Prefetching
- Virtualizing UI

#### Bundle Size Improvements

- Only load the code the user needs (split up bundle)
- Code splitting

#### Images

- Progressive JPEGs (blurry --> crisp)
- Saves 2-10% bandwidth

#### Virtualizing UI

- Load-on-demand/Laz-loading data


## PWA Concepts

- Security
- Caching strategies
- Desktop PWAs
- App Store Availability
- Accessibility


## Tools

- Devtools for First Contentful Paint
- Lighthouse
- Webpack bundle analyzer
- Performance Budget Calculator


## Additional Notes

- Starbucks' PWA and App are incredibly similar


## Questions

- Viewport size vs component size
  - Are your (KendoUI) components self-aware of their size (or of their container)?