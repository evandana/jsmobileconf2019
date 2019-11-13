# Client-Side Data Storage

## Speaker: Raymond Camden

Engineer for [HERE](https://www.here.com/) (Maps and stuff)

[Slides](https://github.com/cfjedimaster/client-side-storage-preso)

## Why Offline Storage?

- Connections aren't boolean
- Some things don't change

## Offline Options

- Cookies
- Web Storage
- IndexDB
- Service Worker & Caching API

### Accessibility

- Supported everywhere
- Storage amounts are not published (except Firefox)

### Cookies

- Safest (as long as it's __your__ cookie)
- Read/Write on Client/Server
- Cookies sent back and forth
- Limited in terms of count and size
- Simple values
- Terrible API

#### How Many?

Browser Spec (Feb 1997)

- 20 per unique host
- 300 cookies (per browser)
- 4096 bytes per cookie

#### Possible Uses

- Auth
- Preferences
- MDN "Simple Cookie Framework"
- others...

### Web Storage

- AKA `localStorage`
- Key/value storage
- Simple values (JASON FTW - casts to STRING)
- `sessionStorage`: Session version (ends when tab closes)
- Remembering form entries across accidental tab close

#### How Much

- 5 MB

#### Methods

- `localStorage.length;`
- `localStorage.clear();`

You can detect when `localStorage` changes (with listener)

#### Libraries

- [Lockr](https://www.lockr.io/)

### IndexedDB

- Not IndexDB
- Storage for "significant amounts of structured data"
- NoSQL (Kinda)
- Async + Transaction API
- Not easy or simple (lots of start up effort)
- [MDN Docs](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API)
- Store binary data! (Sounds!)

#### How Much?

- Max storage space is half your hard drive size

#### Index What?

- Get values based on key
- You can make an index on (most) any property
- And range on an index (think names)
- Outside of indexes, no "search"

#### Getting Started and Demos

(see actual [slides](https://github.com/cfjedimaster/client-side-storage-preso)
)

#### Tools

- Dexie.js
- idb
- localForge

### Service Workers + Cache API

- PWA
- Cache PI lets you read/write to the browser cache
- Keyed by name (think bucket)

#### Choose the Right Cache Strategy

- Push Notifications
- Find the right push strategy for you, then find the right library

#### Service Worker Libraries

- Workbox
- ServiceWorker Cookbook


## How to Use These Tools

- Storage API (for managing client-side storage for a site across IndexedDB, cookies, etc)
- "best-effort" vs "persistent"
- StorageManager
- Chrome Native File System API


## Questions

- Security around hitting limits
- HIPAA for IndexedDB/other storage? BAA? Encryption?