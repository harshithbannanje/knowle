**Intersection between 2 lists**
```
	final List<String> list = Arrays.asList("red", "blue", "blue", "green", "red");
	final List<String> otherList = Arrays.asList("red", "green", "green", "yellow");

	final Set<String> result = list.stream()
		.distinct()
    	.filter(otherList::contains)
    	.collect(Collectors.toSet());
  
```
