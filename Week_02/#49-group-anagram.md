# Description

https://leetcode-cn.com/problems/group-anagrams/

# Solution

## option 1

如果是异位词，每一个字符串先排序，然后他们的字符串将是一样的，然后依次作为key, 用hash表记录下来

```java
// 排序后是一样的字符串
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> map = new HashMap<>();
        for(int i = 0; i < strs.length; i++){
            char[] itemChars = strs[i].toCharArray();
            Arrays.sort(itemChars);
            String key = new String(itemChars);
            List<String> list = map.getOrDefault(key, new ArrayList<>());
            if(list != null){
                list.add(strs[i]);
            }
            map.put(key, list);
        }
        return new ArrayList<List<String>>(map.values());
    }
}
```

时间复杂度：O(nklogk)，其中 n是strs 中的字符串的数量，k是 strs 中的字符串的的最大长度。

空间复杂度：O(nk)O(nk)，其中 n是 strs 中的字符串的数量，k是 strs 中的字符串的的最大长度。需要用哈希表存储全部字符串。

## option 2

因为是小写字母，可以用一个size为26的int数组来记录字符个数，如果是异位词，它们在int数组的记录是一样的，即可以用int数组中的记录的字符+字符个数来作为key记录所有异位词

```java
// 排序后是一样的字符串
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> result = new ArrayList<>();
        Map<String, List<String>> map = new HashMap<>();
        for(int i = 0; i < strs.length; i++){
            char[] itemChars = strs[i].toCharArray();
            int[] record = new int[26];
            for(int j = 0; j < itemChars.length; j++){
                int index = itemChars[j] - 'a';
                record[index] ++;
            }
            StringBuilder stringBuild = new StringBuilder();
            for( int k = 0; k < 26; k++){
                if(record[k] > 0){
                    stringBuild.append('a' + k)
                                .append(record[k]);
                }
            }
            String key = stringBuild.toString();
            List<String> list = map.getOrDefault(key, new ArrayList<>());
            list.add(strs[i]);
            map.put(key, list);
        }
        return new ArrayList<List<String>>(map.values());
    }
}
```

# option 3

用质数表示26个字母，把字符串的各个字母相乘，这样可保证字母异位词的乘积必定是相等的。