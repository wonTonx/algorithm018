# 自己的排序解放(时空奇差)
```
public boolean isAnagram(String s, String t) {
        String[] sArr = s.split("");
        String[] tArr = t.split("");
        Arrays.sort(sArr);
        Arrays.sort(tArr);
        return Arrays.toString(sArr).equals(Arrays.toString(tArr));
    }
```

# 官方优化暴力排序
```
public static boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) {
            return false;
        }
        char[] str1 = s.toCharArray();
        char[] str2 = t.toCharArray();
        Arrays.sort(str1);
        Arrays.sort(str2);
        return Arrays.equals(str1, str2);
    }
```

# 哈希表 利用字母和a的偏移当数组的下标要记得
```
public static boolean isAnagram(String s, String t) {
        if (s.length() != t.length()) {
            return false;
        }
        int[] table = new int[26];
        for (int i = 0; i < s.length(); i++) {
            table[s.charAt(i) - 'a']++;
        }
        for (int i = 0; i < t.length(); i++) {
            table[t.charAt(i) - 'a']--;
            if (table[t.charAt(i) - 'a'] < 0) {
                return false;
            }
        }
        return true;
    }
```