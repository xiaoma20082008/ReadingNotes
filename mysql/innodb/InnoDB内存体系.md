## 后台线程

即：InnoDB Background Thread

查询线程信息：`select * from information_schema.threads`;

主要包括：

    IO Thread
        Read Thread
        Write Thread
    Insert Buffer Thread
    Log Thread

    Master Thread
    Purge Thread
    Latch Monitor Thread
    Page Cleaner Thread

## BUFFER_POOL