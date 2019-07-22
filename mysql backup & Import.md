匯出：
mysqldump -u root -p [來源資料庫] > [備份資料庫路徑.sql];

mysqldump -u root -p toppy368_user > toppy368_user20160806.sql;

匯入：
mysql -u root -p [匯入的資料庫目的地] < [來源資料庫路徑.sql];

mysql -u root -p toppy368_user < toppy368_user20160806.sql;

注意：請先創好空的資料庫才能匯入
