点击上方**蓝字****"码辣架构****"关注我**

 每周至少一篇精品技术文章准时送上！

猜您喜欢

往期精选▼

[1\. 作为程序员你是如何学习的？](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483673&idx=1&sn=e479d2cc40198ea654c8a8883b551049&chksm=fe6d0a7ec91a83686218923a478f7856269912e9236384a53accdbb392606ccd84b6fcbbc130&scene=21#wechat_redirect)

[2.](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483663&idx=1&sn=6c17c7cd1f8c75afe751f931bbd5dfa2&chksm=fe6d0a68c91a837e3151c3e4117af3df917811a7813e0d46f590b746264102675695819bfdfc&scene=21#wechat_redirect) [程序员为什么会有职业瓶颈](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483663&idx=1&sn=6c17c7cd1f8c75afe751f931bbd5dfa2&chksm=fe6d0a68c91a837e3151c3e4117af3df917811a7813e0d46f590b746264102675695819bfdfc&scene=21#wechat_redirect)[？](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483663&idx=1&sn=6c17c7cd1f8c75afe751f931bbd5dfa2&chksm=fe6d0a68c91a837e3151c3e4117af3df917811a7813e0d46f590b746264102675695819bfdfc&scene=21#wechat_redirect)

[3.](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483778&idx=1&sn=705e7442595986ba592cb7e15d5ee847&chksm=fe6d0ae5c91a83f3cf5b13dcdf0ea97617920287f94a3b09768ed2af94c40fd1b033e373c1d9&scene=21#wechat_redirect) [摸鱼式加班，正在毁掉年轻人](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483778&idx=1&sn=705e7442595986ba592cb7e15d5ee847&chksm=fe6d0ae5c91a83f3cf5b13dcdf0ea97617920287f94a3b09768ed2af94c40fd1b033e373c1d9&scene=21&token=584762054&lang=zh_CN#wechat_redirect)

[4.](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483787&idx=1&sn=e31c8e03e8192f1ea7449bb83002528f&chksm=fe6d0aecc91a83fa4d5de7b7838e95b1541108bedf441386de3b470943cc0569a36234598f69&scene=21#wechat_redirect) [分布式系统中接口的幂等性](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483787&idx=1&sn=e31c8e03e8192f1ea7449bb83002528f&chksm=fe6d0aecc91a83fa4d5de7b7838e95b1541108bedf441386de3b470943cc0569a36234598f69&scene=21#wechat_redirect)？

[5.](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483783&idx=1&sn=c9e27b78981bd2ad6c91fed96e24a2d4&chksm=fe6d0ae0c91a83f666c6cbbdf6c132f7b1878027113c3650d4e9908e439ca5afeacd11ff51fc&scene=21#wechat_redirect) [分布式系统中一致性哈希算法](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483783&idx=1&sn=c9e27b78981bd2ad6c91fed96e24a2d4&chksm=fe6d0ae0c91a83f666c6cbbdf6c132f7b1878027113c3650d4e9908e439ca5afeacd11ff51fc&scene=21#wechat_redirect)

HashMap一直是Java面试官喜欢考察的题目，无论应聘者你处于哪个级别，在多轮的技术面试中似乎总有一次会被问到有关 HashMap 的问题。

为什么在Java面试中一定会深入考察HashMap？因为 HashMap 它的设计结构和原理的特点，它既可以考初学者对 Java 集合的了解又可以深度的发现应聘者的数据结构功底。

围绕着HashMap的问题，既可以问的很浅但是又可以深入的聊的很细，聊到数据结构，甚至计算机底层。

我们知道在 Jdk1.7 和 Jdk1.8（及以后）的版本中 HashMap 的内部实现有很大区别，由于目前 Jdk1.8 是主流的一个版本，所以我们在这里只对 Jdk1.8的版本中HashMap 做个讲解。

Jdk1.8 相较于 Jdk1.7 其实主要是在两个方面做了一些优化，使得数据的存储和查询效率有了很好的提升。

*   **存储方面**由原来的`数组+链表`的存储结构变更为`数组+链表+红黑数`的结构，从数据结构知识点中我们知道链表的特点是：寻址（查询）困难，插入和删除容易。随着存储数据的增加，链表的长度会持续增长，查询效率会越来越低，通过转变成红黑树可以提升查询的效率。
    
*   **寻址优化**原来的 Jdk1.7 中通过对 key 值`Hash取模`的方式定位 value 在数组中的下表位置然后存入对应下标中的链表中，查询的时候通过同样的方式获取数据。在Jdk1.8 中对这块做了一个优化，减少哈希碰撞率。
    

要了解 HashMap 我们只需要重点关注它的3个API即可，分别是 put，get和 resize。接下来我们跟踪这3个方法的源码分别进行详细分析。

我们先来看下put方法做了些什么，put方法的入参就两个值：key和value，也就是我们经常使用的，其源码如下

`public V put(K key, V value) {  
    return putVal(hash(key), key, value, false, true);  
}  
`

可以看到具体实现不在这里，里面有个putVal的方法，所有逻辑处理都在putVal方法中。

`final V putVal(int hash, K key, V value, boolean onlyIfAbsent, boolean evict) {  
    //tab: 即table数组，n：数组的长度，i: 哈希取模后的下标，p: 数组下标i存储的链表或者红黑树首节点，   
    Node<K,V>[] tab; Node<K,V> p; int n, i;  
    //table数组为空或长度为0，则调用resize方法初始化数组  
    if ((tab = table) == null || (n = tab.length) == 0)  
        n = (tab = resize()).length;  
    //如果哈希取模后对应的数组下标节点数据为空，则新创建节点，当前k-v为节点中第一条数据   
    if ((p = tab[i = (n - 1) & hash]) == null)  
        tab[i] = newNode(hash, key, value, null);  
    //哈希取模后对应下标节点不为空时  
    else {  
        Node<K,V> e; K k;  
        //如果当前的k-v与首节点哈希值和key都相等，赋值p->e  
        if (p.hash == hash &&  
            ((k = p.key) == key || (key != null && key.equals(k))))  
            e = p;  
        //当前节点为红黑树，按照红黑树的方式添加k-v值  
        else if (p instanceof TreeNode)  
            e = ((TreeNode<K,V>)p).putTreeVal(this, tab, hash, key, value);  
        else {//到这一步，说明节点类型为链表类型，循环遍历链表，这里只是添加新的而不处理同一个元素value的更新  
            for (int binCount = 0; ; ++binCount) {  
                //节点为尾部节点，当前k-v作为新节点并添加到链表尾部  
                if ((e = p.next) == null) {  
                    p.next = newNode(hash, key, value, null);  
                    //当节点数>=8时，则链表转红黑树（TREEIFY_THRESHOLD - 1 = 7，binCount从0开始）  
                    if (binCount >= TREEIFY_THRESHOLD - 1) // -1 for 1st  
                        treeifyBin(tab, hash);  
                    break;  
                }  
                //当前遍历到的节点e的哈希值和key与k-v的相等则退出循环，因为这里只处理新增  
                if (e.hash == hash &&  
                    ((k = e.key) == key || (key != null && key.equals(k))))  
                    break;  
                //当前节点e不为尾结点，将e->p，继续遍历   
                p = e;  
            }  
        }  
        //处理更新操作，新值换旧值  
        if (e != null) { // existing mapping for key  
            V oldValue = e.value;  
            //onlyIfAbsent为false或者旧值为空时，赋新值value  
            if (!onlyIfAbsent || oldValue == null)  
                e.value = value;  
            //空函数，可以由用户根据需要覆盖回调  
            afterNodeAccess(e);  
            //返回旧值  
            return oldValue;  
        }  
    }  
    ++modCount;  
    //如果当前map中包含的k-v键值数超过了阈值threshold则扩容  
    if (++size > threshold)  
        resize();  
    //空函数，可以由用户根据需要覆盖回调  
    afterNodeInsertion(evict);  
    return null;  
}  
`

阅读完putVal的源码后，我们得到如下一些知识点：

1.  新值添加到链表尾部，如果链表长度达到8的时候，链表会转换为红黑树，优化了链表查询慢的问题。后续在resize中可以知道长度降到6的时候，红黑树会转为链表。
    
2.  map中k-v键值总数超过阈值（threshold）的时候会进行扩容，而 threshold的值是在resize里面计算的，初始化值为`(int)(DEFAULT_LOAD_FACTOR * DEFAULT_INITIAL_CAPACITY)`即 `16*0.75=12`。从putVal方法中可以看到共有两次调用`resize()`，分别是初始化和扩容的时候。
    

putVal方法有5个入参，第一个入参似乎调用了一个hash方法传参是key。我们先看下这个 hash 方法。

`static final int hash(Object key) {  
    int h;  
    return (key == null) ? 0 : (h = key.hashCode()) ^ (h >>> 16);  
}  
`

当key为空时直接返回0，这个我们能看懂。当key不为空时，那一串是啥？干啥的？它将key的hashCode值和hashCode值右移16位后进行异或运算。为什么要这样运算呢？看着有点莫名其妙。

其实**这里就是 Jdk1.8 对寻址的优化，这样做有什么好处呢？**

HashMap中是通过对 key 的哈希取模后的值定位到数组的下标位置的，但是`hash(key) % length`的运算效率很低，在数学中`hash(key) & (n - 1)`的结果是跟`hash(key) % n`取模结果是一样的，但是与运算的性能要比hash对n取模要高很多。因此在源码中的`tab[i = (n - 1) & hash]`就是对数组长度做哈希取模运算。

但是这里哈希运算没有直接用 key 的 hashCode 值，而是做了一个右移16位再异或的运算`(h = key.hashCode()) ^ (h >>> 16)`，这样做的目的又是什么呢？

对象的 hashCode 是一个 int 类型的整数，假设 key 的 hashCode 值是 h=514287204853，将其转为二进制格式

![](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

两者进行异或运算，得到哈希值hash，注意观察hash值的特点

![](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

h右移16位意味着将高16的值放在了低16位上，高16位补0，这样处理后再与h进行异或运算得到一个运算后的hash值。

从结果中可以得知，运算后的hash值和原来的hashCode值相比，高16位还是原来h的高16位，而低16位则是原来的高16位和低16的异或后的新值。

将这样的得到的hash值再与(n-1)进行与运算，n即为数组的长度，初始值是16，每次扩容的时候，都是2的倍数进行扩容，所以n的值必不会很大。它的高16位基本都为0，只有低16位才会有值。下面以 n=16 为例讲解。

![](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

由于 (n-1) 的高16位都为0，所以任何和它进行与运算的数据值，运算后的结果index的高16位都不会受影响必为0，只有低16位的结果会受影响。这样高16位相当于没什么作用。

![](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

这样会造成什么问题呢？如果两个对象的hashCode值低16位相同而高16位不同，那么它们运算后的结果必相同，从而导致哈希冲突，定位到了数组的同一个下标。

![](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

而通过右移16位异或运算后，相当于是将高16位和低16位进行了融合，运算结果的低16位具有了h的高16位和低16位的联合特征。这样可以降低哈希冲突从而在一定程度上保证了数据的均匀分布。

看完 putVal 的源码后，我们了解到了存储结构和哈希寻址的优化，但是还存在着一些疑惑没有解开

**为什么要链表和红黑树的转换？**

链表和红黑树的转换是基于时间和空间的权衡，链表只有指向下一个节点的指针和数据值，而红黑树需要左右指针来分别指向左节点和右节点，TreeNodes 占用空间是普通 Nodes 的两倍，因此红黑树相较于链表需要更多的存储空间，但是红黑树的查找效率要优于链表。

当然这些优势都是基于数据量的前提下的，只有当容器中的节点数量足够多的时候才会转红黑树。数据量小的时候两者查询效率不会相差很多，但是红黑树需要的存储容量更多，因此需要设置一个转换的阈值分别是8和6。

**那为什么阈值分别就是8和6呢？**

这个HashMap的设计者在源码的注释中给予说明了，其实很多的疑惑都可以从源码的阅读中得到答案

`/* Because TreeNodes are about twice the size of regular nodes, we  
* use them only when bins contain enough nodes to warrant use  
* (see TREEIFY_THRESHOLD). And when they become too small (due to  
* removal or resizing) they are converted back to plain bins.  In  
* usages with well-distributed user hashCodes, tree bins are  
* rarely used.  Ideally, under random hashCodes, the frequency of  
* nodes in bins follows a Poisson distribution  
* (http://en.wikipedia.org/wiki/Poisson_distribution) with a  
* parameter of about 0.5 on average for the default resizing  
* threshold of 0.75, although with a large variance because of  
* resizing granularity. Ignoring variance, the expected  
* occurrences of list size k are (exp(-0.5) * pow(0.5, k) /  
* factorial(k)). The first values are:  
*  
* 0:    0.60653066  
* 1:    0.30326533  
* 2:    0.07581633  
* 3:    0.01263606  
* 4:    0.00157952  
* 5:    0.00015795  
* 6:    0.00001316  
* 7:    0.00000094  
* 8:    0.00000006  
* more: less than 1 in ten million  
*/  
`

当理想情况下，即哈希值离散性很好、哈希碰撞率很低的时候，数据是均匀分布在容器的各链表中，不会出现数据比较集中的情况，这时候红黑树是没必要的。但是现实中每个对象的哈希算法随机性高，因此就可能导致不均匀的数据分布。

之所以选择8是从概率的角度提出的，理想情况下，在随机哈希码算法下容器中的节点遵循泊松分布，在Map中一个链表长度达到8的概率微乎其微，可以看到8的时候概率是0.00000006，如果这种低概率的事都发生了说明链表的长度确实比较长了。至于为什么不选择同一个值作为阈值是为了缓冲，可以有效防止链表和红黑树的频繁转换。

其实看懂了 putVal 再看 get 获取值的时候就感觉很简单了，首先看 `get(Object key)`

`public V get(Object key) {  
    Node<K,V> e;  
    return (e = getNode(hash(key), key)) == null ? null : e.value;  
}  
`

这里不是具体实现，获取的逻辑在 getNode 方法中，这里同样的会调用 hash(key)方法，找到 key 对应的数组下标位置。

`final Node<K,V> getNode(int hash, Object key) {  
    Node<K,V>[] tab; Node<K,V> first, e; int n; K k;  
    //数组不为空且数组长度大于0且定位到的下标位置节点不为空  
    if ((tab = table) != null && (n = tab.length) > 0 &&  
        (first = tab[(n - 1) & hash]) != null) {  
        //如果当前key存储在首节点则直接返回  
        if (first.hash == hash && // always check first node  
            ((k = first.key) == key || (key != null && key.equals(k))))  
            return first;  
        //如果不是首节点则继续遍历  
        if ((e = first.next) != null) {  
            //如果是红黑树结构，则按照红黑树的方式获取值  
            if (first instanceof TreeNode)  
                return ((TreeNode<K,V>)first).getTreeNode(hash, key);  
            //按照链表的方式获取值  
            do {  
                if (e.hash == hash &&  
                    ((k = e.key) == key || (key != null && key.equals(k))))  
                    return e;  
            } while ((e = e.next) != null);  
        }  
    }  
    return null;  
}  
`

整个 hashMap 就扩容的这块相对来说是最复杂的了，涉及到数据的迁移和重新寻址，代码量也比较多，需要点耐心。

`final Node<K,V>[] resize() {  
    Node<K,V>[] oldTab = table;  
    int oldCap = (oldTab == null) ? 0 : oldTab.length;  
    int oldThr = threshold;  
    int newCap, newThr = 0;  
    if (oldCap > 0) {  
        //如果容量已经达到最大值了，这时候也无法扩容了，所以就将阈值也调到最大，然后返回原数组  
        if (oldCap >= MAXIMUM_CAPACITY) {  
            threshold = Integer.MAX_VALUE;  
            return oldTab;  
        }  
        //将容量扩大两倍，同时阈值也扩大两倍  
        else if ((newCap = oldCap << 1) < MAXIMUM_CAPACITY &&  
                 oldCap >= DEFAULT_INITIAL_CAPACITY)  
            newThr = oldThr << 1;  
    }  
    else if (oldThr > 0) // initial capacity was placed in threshold  
        newCap = oldThr;  
    else {//oldCap=0或oldThr=0时，即初始化时的设置   
        newCap = DEFAULT_INITIAL_CAPACITY;  
        newThr = (int)(DEFAULT_LOAD_FACTOR * DEFAULT_INITIAL_CAPACITY);  
    }  
    if (newThr == 0) {  
        float ft = (float)newCap * loadFactor;  
        newThr = (newCap < MAXIMUM_CAPACITY && ft < (float)MAXIMUM_CAPACITY ?  
                  (int)ft : Integer.MAX_VALUE);  
    }  
    threshold = newThr;  
    @SuppressWarnings({"rawtypes","unchecked"})  
    //根据新的容量初始化新的数组  
    Node<K,V>[] newTab = (Node<K,V>[])new Node[newCap];  
    table = newTab;  
    //上面是对容器的扩容，这里开始将原来的容器中的数据迁移到扩容后新的容器中  
    if (oldTab != null) {  
        //遍历原数组容器  
        for (int j = 0; j < oldCap; ++j) {  
            Node<K,V> e;  
            //如果旧的hash桶数组在j结点处不为空，复制给e  
            if ((e = oldTab[j]) != null) {  
                oldTab[j] = null;//将旧的hash桶数组在j结点处设置为空，方便gc  
                //如果e后面没有Node结点，意味着当前数据下标处只有一条数据  
                if (e.next == null)  
                    //将e根据新数组长度做哈希取模运算放到新的数组对应下标中  
                    newTab[e.hash & (newCap - 1)] = e;  
                else if (e instanceof TreeNode)  
                    //如果e是红黑树的类型，那么按照红黑树方式迁移数据，split里面涉及到红黑树转链表  
                    ((TreeNode<K,V>)e).split(this, newTab, j, oldCap);  
                else {  
                    //定义两个新链表lower，higher  
                    Node<K,V> loHead = null, loTail = null;  
                    Node<K,V> hiHead = null, hiTail = null;  
                    Node<K,V> next;  
                    do {  
                        //将Node结点的next赋值给next  
                        next = e.next;  
                        //如果结点e的hash值与原数组的长度作与运算为0，则将它放到新链表lower中  
                        if ((e.hash & oldCap) == 0) {  
                            if (loTail == null)  
                                loHead = e;//将e结点赋值给loHead  
                            else  
                                loTail.next = e;//否则将e赋值给loTail.next  
                            loTail = e;//然后将e复制给loTail  
                        }  
                        //如果结点e的hash值与原数组的长度作与运算不为0，则将它放到新链表higher中  
                        else {  
                            if (hiTail == null)  
                                hiHead = e;//将e赋值给hiHead  
                            else  
                                hiTail.next = e;//如果hiTail不为空，将e复制给hiTail.next  
                            hiTail = e;//将e复制个hiTail  
                        }  
                    } while ((e = next) != null);//直到e为空结束循环，即链表尾部  
                    if (loTail != null) {  
                        loTail.next = null;//将loTail.next设置为空  
                        newTab[j] = loHead;//将loHead赋值给新的hash桶数组[j]处  
                    }  
                    if (hiTail != null) {  
                        hiTail.next = null;//将hiTail.next赋值为空  
                        newTab[j + oldCap] = hiHead;//将hiHead赋值给新的数组[j+原数组长度]  
                    }  
                }  
            }  
        }  
    }  
    return newTab;  
}  
`

跟着读完一遍 resize 的代码后，可以看到代码的前一部分是扩容的代码，扩容的逻辑是新数组的长度是原数组的2倍，但也不是无限扩容，直到长度超过了最大容量值`MAXIMUM_CAPACITY = 1 << 30`停止，这时候也不设置阈值了直接指定阈值为`threshold = Integer.MAX_VALUE`。

后一部分为数据迁移的逻辑，通过for循环遍历原数组，将原数组的数据迁移到新容器中。分为3种情况处理

1.  如果原数组下标处只有一个节点，则将该节点通过对新数组的长度哈希运算`hash&(newCap - 1)`定位到新的下标位置。
    
2.  如果原数组下标处的节点是红黑树结构，则调用`split()`方法进行数据迁移，如果数据节点少于6的话，里面会将红黑树转链表。
    
3.  如果原数组下标处的节点是链表，则按照链表的方式进行数据迁移。
    

**迁移后的数据位置会变化吗？**

红黑树和链表的数据迁移不是规规矩矩的按照原容器的样式进行迁移的，它这里定义了两个新的节点，链表的时候是 `Node<K,V> loHead = null, loTail = null; Node<K,V> hiHead = null, hiTail = null;`，而红黑树的时候是`TreeNode<K,V> loHead = null, loTail = null;TreeNode<K,V> hiHead = null, hiTail = null;`，其中 lo 应是 lower 的缩写，hi 应是 higher 的缩写。这样做的原因按照源码中的话就是`because we are using power-of-two expansion`。

所以原数组某个下标处的节点链中的数据迁移的时候会被拆分成两部分，这里以链表为例来说明，它会将节点的hash和原数组长度做个与运算(`e.hash & oldCap`)，如果结果为0，则放到链表 lower 中，否则放到链表higher中。

链表 lower 存放的下标在新数组中不变，即原来是`oldTab[4]`，则新数组中是`newTab[4]`。链表 higher 会在原下标的基础上加上原数组的长度，即原来是`oldTab[4]`，则新数组中是`newTab[4+ oldCap]`。

最后再说一点，**你知道为什么要扩容吗？**

其实很简单的原因，这得从数组的数据结构说起了，我们常说数组的查询快，这种说法是基于下标寻址来说的，由于数组中的元素在内存中是连续存储的，当我们定义好数组的长度后这个数组就固定了不能再改变它，计算机会在内存中分配一整块连续的空间给它，由于是连续的所以我们知道a\[0\]的地址，通过加n就知道a\[n\]的地址了。由于这个特性所以如果原数组满了，那么必须在内存中开辟一个新的数组然后将数据从原数组中迁移过来。

HashMap 的源码和重点的知识点我们都已经过了一遍，可以看到一个简单的集合容器内部包含了设计者的丰富思想和技术能力。我们阅读源码既能帮助我们了解这个知识点并更好的使用它，又可以从中学习到设计思想以便我们工作中可以借鉴使用，可见阅读源码的重要性

![](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)

● [作为程序员你是如何学习的？](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483673&idx=1&sn=e479d2cc40198ea654c8a8883b551049&chksm=fe6d0a7ec91a83686218923a478f7856269912e9236384a53accdbb392606ccd84b6fcbbc130&scene=21#wechat_redirect)

● [程序员为什么会有职业瓶颈](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483663&idx=1&sn=6c17c7cd1f8c75afe751f931bbd5dfa2&chksm=fe6d0a68c91a837e3151c3e4117af3df917811a7813e0d46f590b746264102675695819bfdfc&scene=21#wechat_redirect)[？](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483663&idx=1&sn=6c17c7cd1f8c75afe751f931bbd5dfa2&chksm=fe6d0a68c91a837e3151c3e4117af3df917811a7813e0d46f590b746264102675695819bfdfc&scene=21#wechat_redirect)

● [分布式系统中接口的幂等性](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483787&idx=1&sn=e31c8e03e8192f1ea7449bb83002528f&chksm=fe6d0aecc91a83fa4d5de7b7838e95b1541108bedf441386de3b470943cc0569a36234598f69&scene=21#wechat_redirect)？

● [分布式系统中一致性哈希算法](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483783&idx=1&sn=c9e27b78981bd2ad6c91fed96e24a2d4&chksm=fe6d0ae0c91a83f666c6cbbdf6c132f7b1878027113c3650d4e9908e439ca5afeacd11ff51fc&scene=21#wechat_redirect)？

● [分布式系统中接口的幂等性](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483787&idx=1&sn=e31c8e03e8192f1ea7449bb83002528f&chksm=fe6d0aecc91a83fa4d5de7b7838e95b1541108bedf441386de3b470943cc0569a36234598f69&scene=21#wechat_redirect)？

● [Java API利用SQL查询elasticsearch](http://mp.weixin.qq.com/s?__biz=MzU5NTgxMTg0OA==&mid=2247483718&idx=1&sn=229fba4d50bd05a799c307ebd9e834f6&chksm=fe6d0a21c91a83373fee20a5582e97718f95a5469c396ad80ec7dd0b56f0b7d61d1442c7c79a&scene=21#wechat_redirect)

![](data:image/gif;base64,iVBORw0KGgoAAAANSUhEUgAAAAEAAAABCAYAAAAfFcSJAAAADUlEQVQImWNgYGBgAAAABQABh6FO1AAAAABJRU5ErkJggg==)