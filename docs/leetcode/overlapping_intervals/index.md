# Overlapping Intervals

## Merge Intervals

[https://leetcode.com/merge-intervals](https://leetcode.com/problems/merge-intervals/)

```java title="Solution.java"
class Solution {
    public int[][] merge(int[][] intervals) {
        if (intervals == null || intervals.length == 0) {
            return new int[0][0];
        }
        
        // Sort intervals by their start time
        Arrays.sort(intervals, Comparator.comparingInt(a -> a[0]));
        
        List<int[]> merged = new ArrayList<>();
        int[] currentInterval = intervals[0];
        merged.add(currentInterval);
        
        for (int[] interval : intervals) {
            int currentEnd = currentInterval[1];
            int nextStart = interval[0];
            int nextEnd = interval[1];
            
            // If intervals overlap, merge them
            if (currentEnd >= nextStart) {
                // Update the end time of the current interval to be the maximum of both ends
                currentInterval[1] = Math.max(currentEnd, nextEnd);
            } else {
                // No overlap, add the interval to the result
                currentInterval = interval;
                merged.add(currentInterval);
            }
        }
        
        return merged.toArray(new int[merged.size()][]);
    }
    
    // Utility method to print intervals
    public static void printIntervals(int[][] intervals) {
        System.out.print("[");
        for (int i = 0; i < intervals.length; i++) {
            System.out.print("[" + intervals[i][0] + ", " + intervals[i][1] + "]");
            if (i < intervals.length - 1) {
                System.out.print(", ");
            }
        }
        System.out.println("]");
    }
}
```

[DeepSeek Link](https://chat.deepseek.com/a/chat/s/cd7f2222-8623-47e8-9ec0-2d46a0b2aa4b)