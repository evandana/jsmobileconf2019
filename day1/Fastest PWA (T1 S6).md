# How to Build the Fastest PWA

## Presenter: Ishan Anand

## Context: Moovweb


## Summary

- Speed is the # value proposition
- Probably measuring the performance incorrectly
- Full stack coordination (with CDN)
- Best techniques
  - Proper cahce management
  - Server Side Rendering (SSR)
  - Prefetching
  - AMP

Framing "Let's deliver the fastest app possible using PWA technologies"

Check out Next.JS


## Properly Measuring Speed

**USE Last Image Rendered**

- Use the **Good Perceptual** Metrics
  - Visual complete time
  - Last image render
  - First Contentful Paint
  - Largest Contentful Paint (largest contentful thing on page)
- Aoid the **Bad Perceptual** Metrics
  - TTI (Time to Interactive) is likely to be a _false negative_
    - Heuristic based on _Network Quiet_ and _CPU Quiet_
    - Prefetching can cause TTI to look bad even though it's better user experience

### Tools: Lighthouse

#### Problems

See if the components are applicable to you

- **Lighthouse Score is relative to the user's machine**
- Score is an arbitrary weighting based on TTI (which, as discovered above is not a good measure)
- Can't measure browsing speed

### Tools: Page Speed Insights

#### Problems

- Score is a result of a 30 Day **moving average**
- Can't measure browsing speed for a SPA
  - Non-SPA to SPA, will be a false negative and make results look bad

### Tools: Web Page Test

#### Needs manual verification for metrics

- Can measure browser speed

### Real User Monitoring

- Measures **First Input Delay**
- Make sure to look at as a histogram
- Can do browser speed measuring with some config-fu

### Network Throttling

- Do this based on your demographics

### Measure Browsing Speed

Use WebPageTest

```
logData 0
navigate https://google.com
// give time for page to settle, prefetch
sleep 3
logdata 1
execandwait ...
```

### Tool: Firebase

```
componentDidMount() {
  // compat with Server-side-render
  const firebase = require('firebase/app')
  // call for start tracking
  // call trace.start()
}

componentDidUpdate() {
  // figure out when done loading
  // call trace.stop()
}
```


## Optimize

### Optimize bundle

- Analyze your JS bundle Size
- Add to CI/CD process

### Tree shaker

- Remove unused JS (dead code)
  - Help it know what to remove
- Different syntax for specific packages: `import get from 'lodash/get'`
- Check if Babel is outputting CommonJS 

### Code Splitting

- Break the bundle into chunks
- Break on:
  - Component boundary
  - Page boundary
- Use a HoC to 

#### Tools for Code Splitting

- Reactt.lazy()
- react-loadable (no longer maintained)

## CSR vs SSR (Client Side vs Server Side)

- SSR requires Hydration
  - Splits viewable from interactive
  - Displays page content faster (no waiting for JS to download and run)
  - Better SEO
    - JS pass uses up the crawl budget (Google running the JS on your page by the Google crawler)

### SSR is Hard

- Requries refactoring client side assumptions
  - No Lifecycle methods (`componentDidMount`)
  - No `window` or `document` objects

- Use a framework
  - React storefront

- Abstract from ReactRouter so Node can understand the routes

**Requires BFF (Node.js) to be cached at CDN**

Problems for caching
- Item cart count can prevent caching
- Users logged in state
- Product recommendations

### Take Aways

- Use it at the start
- Use a framework


## CDN and Cache Management

- Without CDN, you can't use SSR

### Requiring custom cache keys

- Localization / Internationalization (based on cookie)
- Custom headers / Segmentation
- User-agent: Incompat. vs Modern Browsers
- A / B Testing

### Normalizing Your Cache

- Marketing campaign tracking parameters on URL will unintentionally bust a cache key
- Manage with cache control headers

### Manage Browser cache and CDN cache

- CDN-as-Code in React Storefront

### Measure Speed

- Measure cache hitrate


## Accelerating Browsing Speed

### Visibility-Based Prefetching

- Detect when link is in the viewport (react-visibility-sensor / IntersectionObserver)
- Use service worker to prefectch
- Prefetch JS chunks and API data to render linked page
- Pause prefetching appropriately to prevent unnecessary traffic

### Watch out for unstructured "CMS Content"

### Machine-Learning Based Prefetching

- Guess.js
- React Storefront Extensions

### Prefetching without a CDN is deadly

- User scrolling a page would make 10x more request than normal (costing network calls and server effort)

### Lazy Load Images and Components Below the Fold

- Use for "expensive" images/content

- `<Lazy><ExpensiveComponent /></Lazy>`: Specify final layout height for slow components to get good layout stability

### Skeletons and Data Reuse

- Show "templates" during loading
- If looking at catalog, pull info from catalog page to detail page if possible

### Minimize Unnecessary Renders

- Use React DevTools to highlight renders
- `PureComponents` or `componentShouldUpdate`
- React `Hooks` can be wasteful without `Memo`ization
- Consider Mobx - components only rerender when observed props change

## AMP

- Does all of the above
- No network latency since prefetched by Google

### Problems

- Almost no JS

### PWA

- Almost all JS

### Managing AMP at Scale

- Set up a pipeline to convert React codebase into AMP and do validation

### Keep your AMPs DRY