# DB


# ２相コミットメント
- 一相コミットメントでは，あるトランザクション処理が発生して，複数のデータベースが更新されたときに片方がエラーを起こしてしまうと，更新処理に矛盾が起きてトランザクション処理の原則（ACID特性）である「原子性」と「一貫性」を満たさなくなってしまう。

![](../../PICTURE/DB/commit1.png)

- ２相コミットメントでは「確定することもできるし」「元に戻すこともできる」状態であるセキュア状態を作り出すことで，片方に異常が起こった場合にロールバックを可能にする。

![](../../PICTURE/DB/commit2.png)

![](../../PICTURE/DB/2Commit_01.png)
![](../../PICTURE/DB/2Commit_02.png)
![](../../PICTURE/DB/2Commit_03.png)
![](../../PICTURE/DB/2Commit_04.png)
