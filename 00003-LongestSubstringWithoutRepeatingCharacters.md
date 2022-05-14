> Given a string s, find the length of the longest substring without repeating characters.

```go
func lengthOfLongestSubstring(s string) int {
    if len(s) <= 1{
        return len(s);
    }
    left, right, ret := 0,0, 1;
    indexes := make(map[byte]int, len(s))

    for right < len(s){
        if idx, ok := indexes[s[right]]; ok {
			left = max(left, idx+1)
		}
        ret =max(ret,right-left+1);
        indexes[s[right]] = right;
        right++;
    }
    
    return ret;
}


func max(a int, b int) int {
	if a > b {
		return a
	}
	return b
}
```