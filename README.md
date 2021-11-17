//字典
typedef struct dict {

    // 类型特定函数
    //type 属性是一个指向 dictType 结构的指针， 每个 dictType 结构保存了一簇用于操作特定类型键值对的函数， Redis 会为用途不同的字典设置不同的类型特定函数
    dictType *type;

    // 私有数据
    //privdata 属性则保存了需要传给那些类型特定函数的可选参数
    void *privdata;

    // 哈希表
    //ht 属性是一个包含两个项的数组， 数组中的每个项都是一个 dictht 哈希表， 一般情况下， 字典只使用 ht[0] 哈希表， ht[1] 哈希表只会在对 ht[0] 哈希表进行 rehash 时使用
    dictht ht[2];

    // rehash 索引
    // 当 rehash 不在进行时，值为 -1，记录了rehash目前的进度
    int rehashidx; /* rehashing not in progress if rehashidx == -1 */
    //rehash 有关的属性就是 rehashidx ： 它记录了 rehash 目前的进度， 如果目前没有在进行 rehash ， 那么它的值为 -1

} dict;

//dictType 字典结构体中属性
typedef struct dictType {

    // 计算哈希值的函数
    unsigned int (*hashFunction)(const void *key);

    // 复制键的函数
    void *(*keyDup)(void *privdata, const void *key);

    // 复制值的函数
    void *(*valDup)(void *privdata, const void *obj);

    // 对比键的函数
    int (*keyCompare)(void *privdata, const void *key1, const void *key2);

    // 销毁键的函数
    void (*keyDestructor)(void *privdata, void *key);

    // 销毁值的函数
    void (*valDestructor)(void *privdata, void *obj);

} dictType;


//哈希表，它是实现字典的底层结构
typedef struct dictht {

    // 哈希表数组,每个table指向dictEntry的指针
    //dictEntry table 默认是4,可以通过修改源码调整
    dictEntry **table;

    // 哈希表大小
    unsigned long size;

    // 哈希表大小掩码，用于计算索引值
    // 总是等于 size - 1
    unsigned long sizemask;

    // 该哈希表已有节点的数量(注意是节点)
    unsigned long used;

} dictht;

//哈希表节点，每个节点保存一个键值队
typedef struct dictEntry {
    // 键
    void *key;
    // 值
    //键值对的值可以是一个指针， 或者是一个 uint64_t 整数， 又或者是一个 int64_t 整数
    union {
        void *val;
        uint64_t u64;
        int64_t s64;
    } v;

    // 指向下个哈希表节点，形成链表
    //有多个hash键分配到同一个索引位置，dictEntry节点的next组成单链表连接起来，解决hash冲突
    struct dictEntry *next;

} dictEntry;