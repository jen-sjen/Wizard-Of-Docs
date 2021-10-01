# Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

# PROGRAM: In python
def merge(intervals):
        if intervals==[]:
            return []
        result=[]
        intervals.sort()
        for interval in intervals:
            if result==[] or result[-1][1]<interval[0]:
                result.append(interval)
            else:
                result[-1][1]=max(result[-1][1],interval[1])
        return result

if __name__ == "__main__":
    intervals=[[1,3],[2,5]]
    print(merge(intervals))

# EXAPLINATION:
In the following problem, 
1) Firstly, Sort the given list according to the start time mentioned in "intervals[i] = [starti, endi]".
2) Traverse sorted intervals starting in iteration(for loop), 
      a) If the result is empty or the current interval endtime is less than the start of the interval interator, then add the interval directly to the result as they don't overlap     
      b) else change the end time of current interval with the largest of the two intervals end times possible.
      
      
 For example, let the given set of intervals be {{1,5}, {3,6}, {9,11}, {10,18}}. The intervals {1,5} and {3,6} overlap with each other, so they should be merged and become {1, 6}. Similarly, {9,11} and {10,18} should be merged and become {9, 18}
 
# Other examples:
Input: intervals = [[1,7],[2,6],[8,11],[9,15]]
Output: [[1,6],[8,15]]
Explanation: Since intervals [1,7] and [2,6] overlaps, merge them into [1,6].Similarly, merge intervals [8,11] and [9,15] to [8,15]

Input: intervals = [[1,10],[10,15]]
Output: [[1,15]]
Explanation: Intervals [1,10] and [10,15] are overlapping at the number 10, merge the intervals to [1,15].
