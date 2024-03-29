---
title: Merge Intervals
date: "2020-06-16T22:12:03.284Z"
tags: ["Array", "Sort"]
description: 2 Sum

status: todo
---

Given an array of intervals where intervals[i] = [starti, endi], merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the intervals in the input.

Example 1:

Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlaps, merge them into [1,6].
Example 2:

Input: intervals = [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considered overlapping.

```javascript
/**
 * @param {number[][]} intervals
 * @return {number[][]}
 */
var merge = function (intervals) {
  intervals.sort((a, b) => a[0] - b[0])
  var i = 1
  var x = intervals[0][0]
  var y = intervals[0][1]
  var out = []

  while (i < intervals.length) {
    if (intervals[i][0] <= y) {
      x = Math.min(x, intervals[i][0])
      y = Math.max(y, intervals[i][1])
    } else {
      out.push([x, y])
      x = intervals[i][0]
      y = intervals[i][1]
    }
    i++
  }
  out.push([x, y])

  return out
}
```
