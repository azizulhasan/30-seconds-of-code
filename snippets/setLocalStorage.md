---
title: setLocalStorage
tags: object
expertise: intermediate
firstSeen: 2022-03-03T05:00:00-04:00
---

Set localStorage based on given `object` and return it as object.

- First of all, check the parameter of the function.
- If it is `null/undefined/array/string` then return. because we are expecting here only an object.
- If `data` is an object but an empty object then also return;
- If the `data` object has a key, then loop through it and set `localStorage` 
- Then store all `localStorage` into `storage` variable. And loop through it. 
- If any `key` is matches with the `data` objects key then get `localStorage`.
- And then store it `storageData` object if not empty.
```js
const setLocalStorage = (data = {}) => {
if (
    data === "undefined" ||
    data === null ||
    data === "" ||
    Array.isArray(data) ||
    typeof data === "string" ||
    (typeof data === "object" && Object.keys(data).length === 0)
  )
    return;
    
  Object.keys(data).map((key) => {
    if (data[key]) {
      window.localStorage.setItem(key, data[key]);
    }
  });

  let storageData = {};
  let storage = window.localStorage;
  for (let key in storage) {
    if (data.hasOwnProperty(key)) {
      let keyData = window.localStorage.getItem(key);
      if (keyData) {
        storageData[key] = keyData;
      }
    }
  }

  return storageData;
  
};
```

```js
setLocalStorage({name: "hasan", email: "hasan@gmail.com"}); //{name: "hasan", email: "hasan@gmail.com"}
```