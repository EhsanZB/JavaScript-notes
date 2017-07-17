## Storage

> web applications can use browser APIs to store data locally on the user's computer (give the web browser a memory!)

* client-side storage is `segregated by origin` (pages from one site can not read the data stored by pages from another site).
* Storage object is a `persistent associative array` that maps string keys to string values.
* difference between `localStorage` and `sessionStorage` has to do with `'life-time'` and `'scope'` --> `'how long'` data is saved and for `'who'` the data is accessible to.
* note that `browsers only allows to store strings` (if we want to store any other type we need to encode and decode by ourself programmatically).
* data stored through localStorage is `permanent` (it does not expire and remains stored on the user's computer), until web app delete it or manually delete by the user.

> localStorage is scoped to the `document origin`.

* remember that in same-origin policy document is defined by its `protocol`, `hostname` and `port`.
* all documents with the same origin `share the same localStorage data` (regardless of the script that actually access localStorage).
* documents with different origins can `never` read or write or overwrite each other's data.

> localStorage is also scoped by `browser vendor`

* for example we visit a site with Firefox and then visit again using Chrome. so the data stored in the visit with Firefox will not be accessible during the second visit by Chrome.

```js
// localStroage syntax:
myStorage = localStorage;

// sessionStorage syntax:
// Save data to sessionStorage
window.sessionStorage.setItem('key', 'value');

// Get saved data from sessionStorage
var data = sessionStorage.getItem('key');
```

> both local and session storages are scoped to the document origin so that documents with different origins will never share storage.

* in addition of this matter, sessionStorage also is scoped on a per-window basis
* it means that if a user has 2 browser tabs displaying documents from same origins -> those 2 tabs have `separate sessionStorage` data.

> data stored in `localStorage has no expiration set`, data stored in `sessionStorage gets cleared` when the page `session ends`.

* A page session lasts for as long as the browser is open and survives over page reloads and restores.
* Opening a page in a new tab or window will cause a new session to be initiated.

> storage API -> `setItem()`, `getItem()`, `removeItem()`, `clear()`,` length`,` key()`

* note that if a browser has 2 tabs open to pages with same origin (and one of those pages stores a value in localStorage, the other tab will receive a storage event. --> such storage events are `only triggered` when storage actually changes.

> sessionStorage is scoped to `top-level window`, so storage events are only triggered for sessionStorage changes when there are '`frames' involved`.

* the event object associated with storage event has 5 properties:

    - key,
    - newValue,
    - oldValue,
    - storageArea(local/session),
    - url

* localStorage and storage event can `serve as a broadcast mechanism` by which a browser send a message to `all windows` that are currently visiting the same website.

#### Cookies
