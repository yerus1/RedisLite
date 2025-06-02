
```java
@Service
public class KVStoreService {

  private final LRUCache cache = new LRUCache(100); // capacity = 100

  public String get(String key) {
    return cache.get(key);
  }

  public void put(String key, String value, long ttlMillis) {
    cache.put(key, value, ttlMillis);
  }

  public void delete(String key) {
    cache.delete(key);
  }

  public boolean contains(String key) {
    return cache.get(key) != null;
  }

  public List<String> getAllKeys() {
    List<String> keys = new ArrayList<>();
    for (Map.Entry<String, Node> entry : map.entrySet()) {
        if (!entry.getValue().isExpired()) {
            keys.add(entry.getKey());
        }
    }
    return keys;
}

  public Map<String, String> getAllValidEntries() {
    Map<String, String> result = new HashMap<>();
    for (Map.Entry<String, Node> entry : map.entrySet()) {
        if (!entry.getValue().isExpired()) {
            result.put(entry.getKey(), entry.getValue().value);
        }
    }
    return result;
}
}
```

```Technologies
Java 
Spring Boot
HashMap
LinkedList
Custom Node Class
```
