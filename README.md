# dsacc

### 1  Basic Data Structure

#### 1.1 Stack



#### 1.2 Queue



#### 1.3 String

```c++
// KMP
next[1] = 0;
for (int i = 2, j = 0; i <= m; i ++) {
	while (j > 0 && p[i] != p[j + 1]) j = next[j];
	if (p[i] == p[j + 1]) j++;
	next[i] = j;
}

for (int i = 1, j = 0; i <= n; i++) {
	while (j > 0 && (j == n || s[i] != p[j + 1])) j = next[j];
	if (s[i] == p[j + 1]) j++;
	f[i] = j;
	// if (f[i] == m), this marks an occurrence of A in B
}
```



##### Robin-Karp

```C++
// const int mod = (1 << 16) + 1; 
// P = 131 or 13331
p[0] = 1;
for (int i = 1; i <= n; i ++) {
    p[i] = p[i - 1] * P % mod;
    h[i] = h[i - 1] * P % mod + (s[i - 1] - 'a' + 1);
}

long long get_hash(int l, int r) {
    long long res = h[r] - h[l - 1] * p[r - l + 1] % mod;
    return (res + mod) % mod;
}
```



#### 1.4 Hash



#### 1.5 Heap



#### 1.6 Trie

```c++
class Trie {
public: 
    Trie() { root = new Node(); }
    void insert(const std::string& word) {
        auto p = root;
        for (auto c: word) {
            int u = c - 'a';
            if (!p->child[u]) p->child[u] = new Node();
            p = p->child[u];
        }
        p->count ++;
    }
    bool search(const std::string& word) {
        auto p = root;
        for (auto c: word) {
            int u = c - 'a';
            if (!p->child[u]) return false;
            p = p->child[u];
        }
        return p->count > 0;
    }
private:
    class Node {
        int count = 0;
        std::unique_ptr<Node> child[26];
    };
    Node* root;
}

```



#### 1.7 Union find Set



#### 1.8 Binary indexed Tree



#### 1.9 Segment tree



### 2  Basic Algorithm

#### 2.1 Binary search

```c++
// Find the smallest number in the monotonically increasing sequence a that is >= x (i.e., x or its successor)
while (l < r) {
	int mid = (l + r) / 2;
	if (a[mid] >= x) r = mid; else l = mid + 1;
}

// Find the largest number in the monotonically increasing sequence a that is <= x (i.e., x or its predecessor)
while (l < r) {
	int mid = (l + r + 1) / 2; // Must + 1, else r - l == 1, mid = l
	if (a[mid] <= x) l = mid; else r = mid - 1;
}
```

#### 2.2  Sort



#### 3  Search

