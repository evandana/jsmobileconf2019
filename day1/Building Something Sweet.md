# Building Something Sweet - Nathan Walker

> Differences between Android and iOS are like the differences between East Coast and West Coast

### Tip 1: NativeScript with Angular

- Many iOS/Android practices and behaviors can be accomplished more simply on JS
  - Presenting modals, etc.

### Tip 2: Layering Components

- The "Photoshop" approach

  - Lots of layers that are siblings, but are hidden and not rendered (or part of the view hierarchy) until needed

    ```
    <GridLayout>
      <page-router-outlet>
      <sweet-shade-cover>
      <sweet-sugar-drops>
      <sweet-slider-view>
      <sweet-audio-player-overlay>
      ...
    ```

  - Use Z-index to detetermine either statically, or **dynamically**, which layers are shown at which height

  - Using `ngrx` to dispatch actions and handle the interaction between layers

### Tip 3: UX Timing

- Timing of animations adds a level of dynamism and interactivity to your app
- Very important to get *just the right* moment when a coach mark or animation should be displayed
- **What happens when your user navigates away in the middle of an animation delay?**
  - For example, if you have a `setTimeout(..., 2000)` to show a tutorial tooltip on your **home** screen, but as soon as the app launches, the user navigates to a subview?
  - **What do you do?** How do you **not** show that tooltip?
- The solution demonstrated was pulling animation timeouts into a service component that manages "animation sequences" based on a UUID that, when canceled, cancels all subsequent scheduled animations for that "flow"

### Tip 4: Feature Flags

- We already sort of do this at Pear - in this example, it's more about making developer lives easier
- ie. a `PEAR_DEV` flag that disables animations, skips a tutorial/onboarding sequence, etc.
- Dummy accounts, mocking login/registration, etc.