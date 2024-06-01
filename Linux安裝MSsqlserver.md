### 安裝MSsql server in Linux Rocky OS
1.安裝環境：
rocky os 8.6

2. 安裝 mssql-tools：
    - $ sudo su
    - $ curl https://packages.microsoft.com/config/rhel/8/prod.repo > /etc/yum.repos.d/msprod.repo
    - $ exit
添加SQL Server 2019存储库：

sudo curl https://packages.microsoft.com/config/rhel/8/mssql-server-2019.repo -o /etc/yum.repos.d/mssql-server-2019.repo 

sudo curl https://packages.microsoft.com/config/rhel/8/prod.repo -o /etc/yum.repos.d/msprod.repo

3. 安裝 mssql-toolsl：
    - 沒有安裝過
        $ sudo yum install mssql-tools unixODBC-devel -y
    
    - 已安裝舊版的 mssql-tools，請移除所有舊版的 unixODBC 套件。
        $ sudo yum remove mssql-tools unixODBC-utf16-devel

    - 若要更新為最新版本的 mssql-tools，請執行下列命令：
        $ sudo yum check-update
        $ sudo yum update mssql-tools

4. 安裝 mssql-server：
    更新套件 $ sudo dnf update -y
    $ sudo dnf -y install mssql-server 

5. 安裝好所需套件後, 運行 mssql-conf初始化MS SQL 資料庫引擎:
    $ sudo /opt/mssql/bin/mssql-conf setup
    選2

6. 把 /opt/mssql/bin/ 目錄加入 $PATH, 那便不用輸入完整 mssql 指令的路徑:
    $ echo 'export PATH=$PATH:/opt/mssql/bin:/opt/mssql-tools/bin' | sudo tee /etc/profile.d/mssql.sh
    $ 9

7. 在 firewalld 開啟埠號 1433:
    $ sudo firewall-cmd --zone=public --add-port=1433/tcp --permanent
    $ sudo firewall-cmd --reload

8. 測試是否可以連接 SQL Server:
    $ sqlcmd -S localhost -U SA


windows10 安裝sql server2019
https://blog.hungwin.com.tw/windows-server-sql-server-2019-install/