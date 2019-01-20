# 最终可执行文件的生成

    gcc -o targetexc sourcelist objectslists
    以依赖的形式生成
    应用程序存放目录： 
        系统：
        系统管理员：/usr/bin     /usr/local/bin     /opt/
    默认include文件搜索目录：/usr/include/  /usr/include/sys/  /usr/include/linux/
    默认库文件搜索目录: /lib    /usr/lib

    静态库与共享库的本质区别在于参与整个程序的生成过程的位置不同（或者说是连入程序的位置，从哪连入）

## 静态库： .a   也称为归档文件

gcc -o target source /libpat
example:

 ###标准库
 gcc -o foo foo.c /usr/lib/libm.a
 equel
 gcc -o foo foo.c -lm

 ###非标准库+标准库
 example:
 gcc -o x11fred -L/usr/openwin/lib x11fred.c -lX11

 归档库的生成
 1. 编写源代码
    fred.c bill.c
 2. 生成目标文件（中间文件）
    gcc -c fred.c bill.c  (gcc -c *.c)
 3. 编写被包含头文件
    libtest.h
 4. 编写调用库（或者函数的）的源代码
    main.c
 5. 使用最终可执行文件的生成命令测试库
    gcc -o main main.c fred.o bill.o
 6. 生成静态库
    ar  crv libtest.a   fred.o bill.o
 7. 为函数库生成内容表
    ranlib libtest.a
 8. 函数库的使用
    gcc -o program program.c libtest.a  （使用7 保存到标准位置时）
    gcc -o program program.c -L. -ltest (未保存到标准库位置)  -L----表示库搜索目录 -ltest----表示-l+静态库名
    gcc -o program program.c -I. ./libtest.a （未保存到标准库位置）   -I表示自定义搜索头文件搜索目录  可直接根上静态库作为依赖

## 共享库： .so

    查看程序需要的共享库命令
        ldd program

## chapter2 comand

   调用内部命令 （$command)

   1. _break : rm -rf filenamewithregulationunit,cd ,>, for var in currentdirorfilename,if [ test -d "$var"];then break fi;echo 'testcontent' > filename
   2. if [ $varname='testcontent'];then command1 else command2 fi
   3. set ---保存
   4. shift
   5. 



