# Revealing 5 Mysteries of Cross-Platform Apps - Zoe Koulouris Augustinos, Peter B. Smith

### Mystery #1: Deploying

#### iOS Security

- SSL is **required** (this is an Apple-enforced rule)
- Let's Encrypt helps with this

#### Minimum Two Environments

- Dev. vs Production environments
- Test Flight is the means to distribute in-house/enterprise
- Planning for multiple environments (staging, QA, prod, etc.)

#### Custom Webpack

- (code snippets shown of Angular environment)

#### Development Patterns

- Recommended to "skip localhost" and go straight to a dev/staging/QA architecture, only using 'dev' environment for your engineering teams
  - *Craig's commentary: You'll take my localhost from my cold, dead hands...*

### Mystery #2: Shareable Code

#### Under the Hood

- `.tns.ts` 
- Shared components best shared as **abstract classes**

#### Sharing Styles

- You have to account for the fact that iOS has poor support for SVG

#### NGRX

- **Actions** and **reducers** are shareable, **effects** not so much

### Mystery #3: Testing

#### Deployment Commands

- Building the "same" application for two platforms means you (as an engineer) have to maintain two 'scripts' or sets of build arguments
  - Web: `ng build --prod`
  - Mobile: `tsc ...`

### Mystery #4: Set Up

- First step: Choosing a cross-platform structure
  - They chose NativeScript Schematics
- Using Test Flight through Apple was their choice for deploying/testing internally
- All the iOS stuff: certs, app IDs, profiles

### Mystery #5: Debugging

- Specifically: State management
- Console logging was their first approach
  - Doable, but not very easy to read
- There's a devtools plugin
  - Allows you to on-demand (through a UI button) log the state and action to the console

### Conclusions

- Shared apps are effective
- Either xPlat or NS Schematics
- NS 6 is an easy update