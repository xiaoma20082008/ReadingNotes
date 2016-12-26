
InnoDB和MyISAM的cardnality值计算有问题！

1. InnoDb计算时，所有的null值不计算在内
2. MyISAM计算时，所有的null值都不相等。

通过analyze table tb1只能优化InnoDB的，不能优化MyISAM的


参考连接：

[显示](http://www.penglixun.com/tech/database/mysql_show_index_cardinality.html)

[分析](https://www.percona.com/blog/2008/09/03/analyze-myisam-vs-innodb/)