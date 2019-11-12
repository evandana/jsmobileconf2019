# Webpack Performance Trickery

## Presenter: Tommy Parnell

How're your build times?

## Scenario: Car Guru

- 75% on mobile
- 3G connections are increasing (for Car Guru's with expanding market)
- 14 years' old col
- 1 mono-repo
- 124 bundles
- Deploy 1-2 times / day

## Stats

- 1 MB takes 5s on 3G
- Google SEO rakings weighted by page speed
- Next billion users will be those in developing nations with tight data constraints
- Watch: "Who is in charge of the internet?" TED Talk

## Tools

### Chrome User Experience Report

- "CrUX" for short
- Query from Google's Big QUery product
- Search your own URL

### Lighthouse

Audit's tab in Chrome Dev Tool

- Gives a score from 0-100
- MUST run that with throttled wifi

### Source Map Explorer 

Command line tool

- Graph of directory structure of what's in the package, size-wise


### Import-cost

Tells you the cost of the package

## Tips

- Prevent bundles from getting bigger - alert devs on PR commits
  - webpack config: `performance: { maxEntrypointSize: 400000, },`
  - Other tools available
- Package optimization
  - `MomentJS` -> `date-fns`
  - `ClassNames` -> `clsx`
  - `lodash` -> vanilla
- Ensure dependencies are not duplicated _across_ bundles: DLLs
  - webpack config:
    ```
    context: path.resolve('..')
    manifest: require('..')
    name: '_dll',
    ```
  - Extract common dependencies between bundles
  - Ensure React isn't included twice in different bundles
- Prevent duplicate dependencies within _same_ bundle
 - `duplicate-package-checker-webpack-plugin`

### Images

Use `<Picture> <source /> <source /> </Picture>`

- Webp -> Chrome + Firefox
- JPEG XR -> IE
- JPEG 2000 -> iOS/Safari

