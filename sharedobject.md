## shared object libraries:(.so)/\
```
-ctest1.c
void ctest1(int *i)
{
   *i=5;
}
-ctest2.c
void ctest2(int *i)
{
   *i=100;
}
-prog.c
#include <stdio.h>
void ctest1(int *);
void ctest2(int *);
int main()
{
   int x;
   ctest1(&x);
   printf("Valx=%d\n",x);

   return 0;
}

-Compile the library functions: 
#gcc -Wall -fPIC -c ctest1.c ctest2.c
-Generate the shared library: 
#gcc -shared -Wl,-soname,libctest.so.1 -o libctest.so.1.0 ctest1.o ctest2.o  (-This generates the library libctest.so.1.0)
-Move to /usr/lib64/ directory:
#mv libctest.so.1.0 /usr/lib64
#ln -sf /usr/lib64/libctest.so.1.0 /usr/lib64/libctest.so.1
#ln -sf /usr/lib64/libctest.so.1 /usr/lib64/libctest.so
-Compile program for use with a shared library: 
#gcc -Wall -L/usr/lib64 prog.c -lctest -o prog
#./prog
-Investigate error/List library dependencies
#ldd libctest.so
-add program to .bash_profile
-export PATH=$PATH:/opt
-execute from anywhere (prog)
```
