Implement a hash map. With load factor.



```
interface Map<K,V> {
	void put(K key, V value);
	V get(K key);
}
```


```
@Data
@Builder
class MapEntry<K, V> {
	private K key;
	private V value;
}

public class HashMap implements Map<K, V> {
	// Hash map 
	// 1. Find the hash of the key
	// 2. Use a mod function to reduce
	// 3. Put the value in the bucket
	
	final List<List<MapEntry>> buckets = null;
	
	private int BUCKET_SIZE = 10;
	
	public HashMap(){
		init();
	}
	
	void init() {
		buckets = new ArrayList();
	}

	void put(K key, V value) {
		// Assuming key is an object always
		// Compute the hash of the key
		int hash = key.hashCode();
		
		// Find the bucket to store the key
		int bucket = getBucket(hash);
		
		// Store the value in the specified bucket
		MapEntry entry = MapEntry.builder().key(key).value(value).build();
		
		List<MapEntry> entries = buckets.get(bucket);
		
		if (entries == null) {
			List<MapEntry> temp = new ArrayList();
			
			temp.add(entry);
			
			buckets.add(temp, bucket);
		} else {
			// Collision
			temp.add(entry);
		}
		
	}
	
	int getBucket(int hash) {
		return hash % BUCKET_SIZE;
	}
}
```

