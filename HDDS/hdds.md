#论文总结

####Hot Data Identification for Flash-based Storage Systems Using Multiple Bloom Filters(2011 MSST)    
多重布隆过滤器：原始的布隆过滤器只利用一个计数器，多重布隆过滤器将它扩展到N个，按访问的次数依
次更新不同的过滤器，当其中R(指定的阈值)个过滤器都被使用时，该元素被当成热点数据。

####Efficient Identification of Hot Data for Flash Memory Storage Systems(2006 TOS)    
A Multihash-Function Framework：多重Hash函数(K个hash函数), 且布隆计算器由1位变为N位，每次有数据被访问，hash函数映射到的位置的计数器+1，判断热点数据的时候，取计数器的高H位，如果一个数据对应的K个位置的高H位都包含1，则被认为是热点数据。

####Methods for finding frequent items in data streams(2010 VLDBJ)    
寻找数据流中的“频繁”数据：Frequent算法，来源于半数数算法(给定一个序列，找出序列中的出现次数大于一半的数)，Frequent算法将半数数算法一般化，半数数算法找到的是访问频率大于1/2的数据，而Frequent算法能够找到数据流中访问频率大于1/k的所有数据；具体的做法是定义k个计算器，分别统计k个数据的访问次数，每访问1次，计算器+1，若被访问的数据不在k个计数器中，则将所有k个计数器-1，并将计数为0的数据移除。Frequent算法是一个必要性的算法，得到的结果需要进一步验证，论文中结合CountSketch进行验证。

####Efficient Computation of Frequent and Top-k Elements in Data Streams(2005 ICDT)    
找出数据流中“频繁”数据或者Top-k的数据，在counter的基础之上提出bucket的概念，利用bucket管理counter，最后得到的数据包括frequent数据和top-k的数据两类。

####Mining Top-K Frequent Items in a Data Stream with Flexible Sliding Windows(2010 KDD)    
+ Mining Frequent Itemsets in a Stream(2007 ICDM)    
+ Mining frequent items in a stream using flexible windows(2008 IDA)    
与一般的数据流中的热点数据监测不同，本文引入了一种灵活的滑动窗口的方法，具体来说就是实时更新每个数据的频率，然后记录一些关键的频率信息(Border Points)，理论上来说所需要的内存空间和数据量的大小线性相关；实际情况中，并不需要精确的top-k frequent数据，上述的统计过程可以进行合理的剪枝，减少数据的统计量。


