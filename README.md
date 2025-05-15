# dsacc



```c++
next[1] = 0;
for (int i = 2, j = 0; i <= m; i++) { // t
	while (j > 0 && t[i] != t[j+1]) j = next[j];
	if (t[i] == t[j+1]) j++;
	next[i] = j;
}

for (int i = 1, j = 0; i <= n; i++) { // s
	while (j > 0 && (j == m || s[i] != t[j+1])) j = next[j];
	if (s[i] == t[j+1]) j++;
	f[i] = j;
	// if (f[i] == m) t s
}
```

