---
title: "简单数据结构"
datePublished: Thu Feb 01 2024 08:09:38 GMT+0000 (Coordinated Universal Time)
cuid: cls2xr5qr000m0al6cnqvhy8f
slug: 566a5y2v5pww5o2u57ut5p6e

---

* trie（字典树）
    

---

## trie(字典树）

**作用**：实现**字符串**快速的**存储**和**查询**

<div data-node-type="callout">
<div data-node-type="callout-emoji">💡</div>
<div data-node-type="callout-text"><strong>son[父亲的节点值][自己的名字]=儿子的节点值</strong></div>
</div>

```cpp
void insert(char str[])//插入字符串
{
	int p = 0;
	for (int i = 0; str[i]; i++)
	{
		int u = str[i] - 'a';
		if (!son[p][u])son[p][u] = ++idx;//给字符分配节点值
		p = son[p][u];
	}
	cnt[p]++;
}
int query(char str[])//查询某字符串的个数
{
	int p = 0;
	for (int i = 0; str[i]; i++)
	{
		int u = str[i] - 'a';
		if (!son[p][u])return 0;
		p = son[p][u];
	}
	return cnt[p];
}
```

---