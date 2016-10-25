---
layout: default
title:
modal-id: introduction
category: array-helpers
---
The following methods have been made available for you to use in manipulating Array's.

#### shuffle
**expects** Array<br/>
**Returns:** The same array in a different order

#### index
**expects** Array, Index(Integer)<br/>
**Returns:** An ArrayItem at the index provided

#### index_of
**expects** Array, ArrayItem(Object)<br/>
**Returns:** Returns the index as an Integer of a specified ArrayItem

#### selected_by
**expects** Array, Key(String), Value(String/Integer)<br/>
**Returns:** An Array containing all the ArrayItems that match the value of the specified Key

#### sample
**expects** Array<br/>
**Returns:** A random ArrayItem from the original Array

#### delete_by
**expects** Array, Key(String), Value(String/Integer)<br/>
**Returns:** An Array containing all the ArrayItems that did not match the value of the specified Key

#### sort_by
**expects** Array, Key(String), Direction(String)<br/>
**Returns:** The Array passed, sorted by the Key with the desired Direction specified

#### grouped_by
**expects** Array, Key(String)<br/>
**Returns:** The Array passed but with the items grouped by the Key specified

#### join_array
**expects** Array1, Array2<br/>
**Returns:** The result of both Arrays specified after being combined

#### value_in_array_contains
**expects** Array, Value(String/Integer)<br/>
**Returns:** A Boolean if the Array passed contains the Value specified
