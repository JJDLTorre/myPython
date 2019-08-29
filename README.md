# myPython

## Error and fix "libclntsh.so: cannot open shared object file"
```bash
jdelat04@juanlinux ~/Interfolio/src/interfolioRPT
$ python interfoliorpt/main.py | tee -a `date +"%Y-%m-%d__%H-%M-%S"`_uploading_dry_run_bug_fix.log
ERROR:root:DPI-1047: Cannot locate a 64-bit Oracle Client library: "libclntsh.so: cannot open shared object file: No such file or directory". See https://oracle.github.io/odpi/doc/installation.html#linux for help
Traceback (most recent call last):
  File "interfoliorpt/main.py", line 22, in <module>
    main()
  File "interfoliorpt/main.py", line 15, in main
    tco.test_upload_all_surveys_ordered()
  File "./interfoliorpt/interfolio_erpt/ifolio_test/TestClassOperations.py", line 714, in test_upload_all_surveys_ordered
    dw = DataWarehouse(env)
  File "/home/jdelat04/Interfolio/src/interfolioRPT/interfoliorpt/interfolio_erpt/DataWarehouse.py", line 28, in __init__
    self.__create_connections()
  File "/home/jdelat04/Interfolio/src/interfolioRPT/interfoliorpt/interfolio_erpt/DataWarehouse.py", line 34, in __create_connections
    self.cp_connection = cx_Oracle.connect(self.cp_user, self.cp_password, self.cp_db)
cx_Oracle.DatabaseError: DPI-1047: Cannot locate a 64-bit Oracle Client library: "libclntsh.so: cannot open shared object file: No such file or directory". See https://oracle.github.io/odpi/doc/installation.html#linux for help
(env_linux) 
```
```bash
jdelat04@juanlinux ~/Interfolio/src/interfolioRPT
$ export LD_LIBRARY_PATH=/opt/oracle/instantclient_12_1/
$ ls /opt/oracle/instantclient_12_1/
adrci         genezi      libclntshcore.so.12.1  libclntsh.so.12.1  libmql1.so   libocci.so.12.1  libocijdbc12.so  liboramysql12.so  libsqlplus.so  ojdbc6.jar  sdk      SQLPLUS_README  xstreams.jar
BASIC_README  glogin.sql  libclntsh.so           libipc1.so         libnnz12.so  libociei.so      libons.so        libsqlplusic.so   network        ojdbc7.jar  sqlplus  uidrvci
```
