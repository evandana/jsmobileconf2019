# Building User Adaptive Interfaces - AJ Keller

## Track 2 - Lecture 3

### What are User Adaptive Interfaces?

- Main purpose of software is to help you, and main challenge of software is **you**
- Symbiotic computing is computers learning from **you**

### Notion

- A piece of hardware using neural sensors in a headset
- On-device machine learning, using JavaScript API

### Notion API

- Calm API, Kinesis API, raw brainwaves
- VSCode Extension
- Use new technology to minimize the time we have to spend dealing with distractions, or in a high state of mind
  - High state of mind = programming, thinking "hard"
  - We are "knowledge workers"
- Processing is done locally, no cloud/remote processing
- Flow Application (using the Calm API)
  - Goal is to track how "calm" or "in the flow" you are while you're working
    - How much time am I spending (a) really working, (b) just sitting at my desk, or (c) distracted
  - rxJS - mind is continuously producing a stream of data
  - Measuring/scoring a running average of a calm state of mind
  - Calm score is **very oscillatory**
  - API: Disabling notifications when "in flow"
  - API: If you have a meeting coming up (per GCal), use that information to bring you "out of flow" ahead of time
  - API: Historic feedback
    - *Does coffee at 2pm help you?*
    - *Does X hours of sleep help or hurt you?*
    - *Does your standing desk make you more productive?*
    - *Does vacation make me more productive when I come back?*
- **Demo**
  - Lots of charts and graphs and brainwaves