# Lua pairs() Iterator Unexpected Behavior During Modification

This repository demonstrates a subtle bug related to Lua's `pairs()` iterator when used with tables that are modified during iteration.  The core issue stems from the fact that `pairs()`'s behavior is undefined when the table structure changes mid-iteration.  This can manifest as skipped elements or unexpected iteration order.

## Bug Description
The `bug.lua` file contains a function `foo()` that recursively iterates through a nested table using `pairs()`.  Under normal circumstances, this should visit all elements. However, if the table is altered during the iteration (even in a nested call), the iteration might be incomplete or produce unexpected results.

## Solution
The `bugSolution.lua` file demonstrates a safer way to iterate, which avoids potential issues caused by table modifications during iteration. It uses a copy of the table to ensure that the original is not modified during the process.