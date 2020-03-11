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

5. HashMap是怎么解决哈希冲突的？

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


