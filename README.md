#####昨日忽生兴趣，想起同事正在玩的一个炸金花游戏，见他们讨论略有激烈，想来蛮有趣，于是自己也写来玩玩
####纸牌游戏炸金花发牌、牌大小比较、排序
####牌大小计算算法
#####花色不参与大小比较:
- 首先对到手的牌按照牌数字按照由大到小排序
- 牌大小按照牌型分级
- 对于普通牌型，每张牌视为16进制的一个数，A对应14，2对应2，以此类推。牌值即为这幅此16进制牌的10进制大小。
    比如最大的普通牌为AKJ，则AKJ=14x16x16+13x16+11=3803
- 对于对子，先将对子放在牌的前两位，则在最大普通牌大小的基础上，加上对子牌的本身大小。
    对子的本身大小计算，比如最大的对子为AAK，则AAK=14*16+13=237，加上普通牌，即为4040
- 对于顺子，取最小的那个数，加上最大的对子牌值，比如最大的顺子AKQ=12+4040=4052
- 对于同花，先按照普通牌型计算大小，再加上最大的对子牌值。
    比如最大的同花AKJ=3803+4052=7855
- 对于同花顺，取最小的那个数，加上最大的同花牌值，比如：
  AKQ=12+7855=7867
- 对于炸弹，取第一个数，加上最大的同花顺牌值。
    比如AAA=14+7867=7881
    
#####花色参与大小比较:
- 比较规则：在牌数字完全一样的情况下，从最大的牌开始比较，黑桃>红桃>梅花>方片，遇到一个较大的，则结束比较。
- 牌值计算原理：在上面花色不参与大小比较算法的基础上，对花色按照4进制进行花色值计算。并对每副计算出来的牌大小乘以64，为什么乘以64？因为花色的范围为63~0。在不考虑花色参与比较的情况下，乘以64，就是把每个大小相邻的牌型拉开64的间隔，以便于让花色值有发挥的空间哈哈哈哈~
- 如果是炸弹，先将炸弹按花色从大到小排序，保证比如黑桃A红桃A方片A会>红桃A梅花A方片A
    
####如此，就可得对所有的牌值进行了统一的大小计算