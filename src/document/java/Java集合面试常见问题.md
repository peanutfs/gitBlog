###Java集合面试常见问题

1. 常见的集合有哪些？

<details>
  <summary>查看答案</summary>
  <div>
    <p>Collection接口和Map接口是所有集合框架的父接口</p>
    <p>Collection接口主要的子接口有：List和Set</p>
    <p>Map接口的主要实现有：HashMap，Hashtable，LinkedHashMap，TreeMap，ConcurrentHashMap，Properties</p>
    <p>List接口的主要实现有：ArrayList，LinkedList，Vector，Stack</p>
    <p>Set接口的主要实现有：HashSet，TreeSet，LinkedHashSet
  </div>
</details>

2. HashMap与Hashtable的区别？

<details>
	<summary>查看答案</summary>
	<div>
		<table>
			<tr>
				<th>HashMap</th>
				<th>Hashtable</th>
			</tr>
			<tr>
				<td>非同步，线程不安全</td>
				<td>使用了synchronized关键字，线程安全</td>
			</tr>
			<tr>
				<td>允许k-v为null</td>
				<td>不允许k-v为null</td>
			</tr>
			<tr>
				<td>继承AbstractMap类</td>
				<td>继承Dictionary类</td>
			</tr>
		</table>
	</div>
</details>

3. HashMap的put方法的具体流程？

<details>
	<summary>查看答案</summary>
	<link>
	<a href = "https://www.jianshu.com/p/939b8a672070">图片来源</a>
	<img src="../../resources/images/collection/map_put.png" />
</details>

4. HashMap的扩容操纵是怎么实现的？
<details>
	<summary>查看答案</summary>
	<div>
		<p>HashMap的扩容分两种情况</p>
		<ol>
			<li>
			初始化哈希表，采用指定或者默认值方法
			</li>
      <li>
      <p>如果扩容前数组容量超过最大值(2^30)，则不在扩容</p>
			<p>如果没有超过最大值，并且当前容量的两倍也未超过最大值，则扩容为原来的两倍</p>
      </li>
			</ol>
			扩容后将每一个bucket移动到新的bucket当中
	</div>
</details>

5. HashMap是怎么解决哈希冲突的？
<details>
	<summary>查看答案</summary>
	<div>
		<ol>
			<li>什么是哈希？</li>
			<p>Hash，一般翻译为"散列"，也有直译为"哈希"，就是把任意长度的输入通过散列算法变换成固定长度的输出，该输出就是散列值(哈希值)。这种转换是一种压缩映射，不同的输入可能存在相同的输入，所以不可能从散列值来确定唯一的输入值</p>
			<p>所有的散列函数都具有一个特性：根据同一散列函数计算出来的散列值如果不同，那么输入值一定不同，但如果计算出来的散列值相同，输入值不一定相同</p>
			<li>什么是哈希冲突？</li>
			<p>当两个不同的输入通过同一个散列函数计算出相同的哈希值，被称作哈希碰撞(冲突)</p>
			<li>JDK1.8中首先通过两次扰动来降低哈希冲突的概率，然后使用链表法来链接拥有相同的hash值数据，如果链表的长度超过8，则将链表转换为红黑树，来降低遍历的时间复杂度{O(n)>O(logn)}</li>
		</ol>
	</div>
<details>

6. HashMap为什么不直接使用hashCode()处理后的哈希值直接作为table下标？

7. HashMap在JDK1.7和JDK1.8中有哪些不同？

8. 为什么HashMap中String，Integer这样的包装类适合作为Key？

9. ConcurrentHashMap和Hashtable的区别？

10. Java集合的快速失败机制"fail-fast"？

11. ArrayList和Vector区别？
<details>
	<summary>查看答案</summary>
	<div>
		<table>
			<tr>
				<th>ArrayList</th>
				<th>Vector</th>
			</tr>
			<tr>
				<td>非同步</td>
				<td>同步，加了synchronized关键字</td>
			</tr>
			<tr>
				<td>容量扩充规则是（原容量+原容量*2）</td>
				<td>容易扩充规则是2倍原容量</td>
			</tr>
		</table>
	</div>
</details>

12. ArrayList和LinkedList区别？
<details>
	<summary>查看答案</summary>
	<div>
		<table>
			<tr>
				<th>ArrayList</th>
				<th>LinkedList</th>
			</tr>
			<tr>
				<td>底层动态数组</td>
				<td>底层双向链表，实现了List和Deque</td>
			</tr>
			<tr>
				<td>检索效率高，增删效率低</td>
				<td>检索效率低，增删效率高</td>
			</tr>
			<tr>
				<td>动态内存，消耗低</td>
				<td>内存消耗相对高</td>
			</tr>
		</table>
	</div>
</details>

13. HashSet是如何保证数据不可重复的？

14. BlockingQueue是什么？

参考：https://www.jianshu.com/p/939b8a672070


