# Client-side Data Storage - Raymond Camden

### Why Store Anything?

- Websites are getting larger
- Sometimes data doesn't change!

### Technologies

- Cookies (they're *everywhere*)
- Web Storage
- IndexedDB
- Service Worker/Caching API

## Options, How to Use Them

### Cookies
- We can store 300+ cookies per browser
- 4kb+ per cookie
- 20+ per host
### Cookies - Uses
- Authentication/Authorization
- Libraries:
  - MDN "simple cookie framework"
  - `vue-cookies`
### Web Storage
- AKA LocalStorage
- KV storage only
- Simple values only (strings! Use JSON if you want)
- Session version
### IndexedDB - Overview
- _Not IndexDB_
- Storage for significant amounts of structured data
- NoSQL (kinda)
- Async + Transaction API
- Neither easy nor simple
### IndexedDB - How does it work?
- Value lookup by key (think 'primary key')
- Index on (most) any property
- Limited searching (really only index searching)
### IndexedDB - API
- `database` vs `object store` vs `index` vs `key`
### IndexedDB - Getting Started
- Open a DB
- Listen for an event that signals that the DB is ready
- You can define object stores on a per-DB-version basis
- You have to **plan ahead** and know what you want to store
- Migrations need to be written manually, and you _version_ the DB via incrementing the assigned number (you have to handle the logic re: whether a person's DB needs upgrading)
### Service Worker + Cache API
- Service Workers provide async access to the network stack
- Caches are keyed by name
- **Workbox** is a common library for dealing with service workers
### Limits
- Storage API
  - "Best effort" strategy means data is only persistent until something more important comes along