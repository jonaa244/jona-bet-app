self.addEventListener("install", e => {
  e.waitUntil(
    caches.open("bettracker-cache").then(cache => {
      return cache.addAll([
        "bettracker_ultimate.html"
      ]);
    })
  );
});

self.addEventListener("fetch", e => {
  e.respondWith(
    caches.match(e.request).then(response => response || fetch(e.request))
  );
});
