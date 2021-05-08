### White Board Coding questions:

---------------------------------------------------------------------------------------------------------------------------------------------------
1. Given a list of integers, return the 2nd maximum valued element.

---------------------------------------------------------------------------------------------------------------------------------------------------

2. Move the 0's to the end while mainting the order of the elements. Only single traversal of the array is required.

Input : arr[]  = {1, 2, 0, 0, 0, 3, 6}

Output : 1 2 3 6 0 0 0

---------------------------------------------------------------------------------------------------------------------------------------------------

3. Given meetings start time and end time. Find if there are any overlapping of meetings happened

Follow up: Now find out the minimum number of unique Zoom IDs required so that all meetings can be arranged successfully. [Overlapping of meetings will require 2 unique Zoom IDs]

[1, 11] -> count = 1
[3, 5] -> count = 2
[5, 9] -> count = 2
[6, 8] -> count = 3
[10, 11] -> count = 3

unique Zoom IDs are 3

Solution: https://guides.codepath.com/compsci/Scheduling-Meeting-Rooms

---------------------------------------------------------------------------------------------------------------------------------------------------

4. Given a singly linked list, find the middle of the linked list.
For example, if the given linked list is 1->2->3->4->5 then the output should be 3.

Solution: https://github.com/codedecks-in/LeetCode-Solutions/blob/master/Java/middle-of-the-linked-list.java

---------------------------------------------------------------------------------------------------------------------------------------------------

5. If a very large sized file (approx 2GB) is given and we have to read and then stores it into DB. Will there be any Out Of Memory error occurs?
How will you able to achieve this task ?

---------------------------------------------------------------------------------------------------------------------------------------------------

6. Write a program in java 8 which will return the string itself it is present in the list else throw an exception.

```
public static String getGenericStr(String word, List<String> str) {
		
    return str.stream()
              .filter(list -> list.contains(word))
              .findFirst()
              .orElseThrow(RuntimeException::new);
}
```
---------------------------------------------------------------------------------------------------------------------------------------------------

7. Write a program in java 8 to sort elements by frequency in decreasing order

input: {"mouse", "notebook", "keyboard", "mouse", "notebook"}
output: {mouse=2, keyboard=1, notebook=2}

```
public class HackerRankCandidateProgram {

	public static void main(String[] args) {
		List<String> transactions = List.of("mouse", "notebook", "keyboard", "mouse", "notebook");
		groupTransactions(transactions).forEach(element -> System.out.println(element));
	}

	public static List<Map.Entry<String, Integer>> groupTransactions(List<String> transactions) {

		Map<String, Integer> transactMap = new HashMap<>();

		for (int i = 0; i < transactions.size(); i++) {
			if (!transactMap.isEmpty() && transactMap.containsKey(transactions.get(i))) {
				int val = transactMap.get(transactions.get(i));

				transactMap.put(transactions.get(i), val + 1);
			} else {
				transactMap.put(transactions.get(i), 1);
			}
		}

		Comparator<Map.Entry<String, Integer>> comparator = (entry1, entry2) -> {

			if (entry1.getValue() > entry2.getValue()) {
				return -1;
			} else if (entry1.getValue() < entry2.getValue()) {
				return 1;
			} else {
				return entry1.getKey().compareTo(entry2.getKey());
			}
		};

		List<Map.Entry<String, Integer>> arr = new ArrayList<Map.Entry<String, Integer>>(transactMap.entrySet());

		Collections.sort(arr, comparator);

		// System.out.println(arr);

		return arr;
	}
}
```

8. Write a method to check if a input string is valid given a string pattern that specifies valid characters and the order both the strings contain comma separated characters. It returns true if following rules are satisfied

1. All characters in input string appear in pattern string and also appear in same order as the pattern string
2. Characters in input string appear in same order as that in pattern
3. Characters in input string can skip characters from pattern as long as the order of characters is same

If the above rules are NOT satisfied then the method returns false

Examples
System.out.println(validator.validate("DXD", "ABCDEFG")); // false
System.out.println(validator.validate("DEF", "ABCDEFG")); // true
System.out.println(validator.validate("ADEG", "ABCDEFG")); // true
System.out.println(validator.validate("", "ABCDEFG")); // false

