# Const keyword and & in c++
_______________________________

**Const keyword in c++**

1-constant variables

-you can't -after assigning variable to const- change it's value.

-you should initialize it in same step of declaration.

(const int var =10;)

example:

>#include <iostream>
 >using namespace std; 
> 
 >int main(){
> 
 >const int y=13;
> 
 >//y=15; ==> compiling error
> 
 >cout<<y;
> 
 >return 0;
> 
>}

(output=13)

2-const with pointer variables

-there are three ways to use const keyword with a pointer

1-pointer variable point to a constant value.

>#include <iostream>
>using namespace std;
>
>int main(){
>
>int x=10;
>
>char y ='R';
>
>const int*i=&x;
>
>const char*j=&y;
> 
>//*j=6;==> error
> 
>x=9;
> 
>y='H';
> 
>cout<<*i<<" "<<*j;
>}

(output= 9 H)

 
2-const pointer variable point to value

>#include <iostream>
> 
>using namespace std;
> 
>int main(){
> 
>int x=4;
> 
>int z=10;
> 
>char y='R';
> 
>char p='C';
> 
>int*const i=&x;
> 
>char*const j=&y;
> 
>*i=10;
> 
>*j='D';
> 
>//*i=&z;==> error
> 
>//*j=&p;==> error
> 
>cout << *i << " and " << *j<< endl;
> 
>cout << i << " and " << j;
> 
>return 0;
> 
>}
 
(output= 10 and D
 
0x61fefc and D)

 
3-const pointer to const variable

>#include <iostream>
> 
>using namespace std;
> 
>int main(){
> 
>int x=7;
> 
>const int* const i = &x;
> 
>// *i=10; ==>error
> 
>char y='R';
> 
>const char* const j = &y;
> 
>// *j='B'; ==>error
> 
>cout << *i << " and " << *j;
> 
>return 0;
> 
>}
 
(output=7 and R)

 
3-Passing const argument value to non const parameter of a function cause
error.
 
>#include <iostream>
> 
>using namespace std;
>
>int fun(int* y)
> 
>{
> 
>return *y;
> 
>}
> 
>int main()
> 
>{
> 
>int z = 8;
> 
>const int* x = &z;
> 
>cout<< fun(x);
> 
>return 0;
> 
>}

=====>error no output

 
4-constant methods

-When a function is declared as const, it can be called on any type of object,
const object as well as non-const objects.
 
-Whenever an object is declared as const, it needs to be initialized at the time of declaration.
However, the object initialization while declaring is possible only with the help of constructors.

>#include <iostream>
> 
>using namespace std;
>
>class Test {
> 
>int value;
>
>public:
> 
>// Constructor
> 
>Test(int v = 0)
> 
>{
> 
>value = v;
> 
>}
>
>   // "value = 1000; ==> error
>
>int getValue() const {
> 
>return value;
> 
>}
>
>   // a nonconst function trying to modify value
> 
>void setValue(int val) {
> 
>value = val;
> 
>}
>};
>
>int main(){
> 
>Test t(20);
> 
>   // non-const object invoking const function, no error
> 
>cout << t.getValue() << endl;
>    // const object
> 
>const Test t_const(10);
> 
>    // const object invoking const function, no error
> 
>cout << t_const.getValue() << endl;
>
>    // const object invoking non-const function, ==>error
> 
>t_const.setValue(15);
>
>    //non-const object invoking non-const function, no error
> 
>t.setValue(12);
>
>cout << t.getValue() << endl;
> 
>return 0;
> 
>}
 

(output=
20
 
10
 
12)

 
4-constant function parameters & return type

>#include <iostream>
> 
>using namespace std;
>
>  // const int can't be changed
> 
>void fun(const int y)
> 
>{
>  // y = 6; ==>error
> 
>cout << y;
> 
>}
> 
>void fun1(int y){
> 
>  // Non-const value can be change
> 
>y = 5;
> 
>cout << '\n'<< y;
> 
>}
> 
>int main(){
> 
>int x = 9;
> 
>const int z = 10;
> 
>fun(z);
> 
>fun1(x);
> 
>return 0;
> 
>}

(output=10
 
5)

 
1-for constant return type

-the return type of fun() is const ,so it returns a const integer value to us.

>#include <iostream>
> 
>using namespace std;
>
>const int fun(int y)
> 
>{
> 
>y--;
> 
>return y;
> 
>}
> 
>int main(){
> 
>int x = 19;
> 
>const int R = 10;
> 
>cout << fun(x) << '\n' << fun(R);
> 
>return 0;
>
>}
 
(output= 18
 
9)

 
2-for const return type and const parameter

-both return type & parameter of function are const types
>#include <iostream>
> 
>using namespace std;
> 
>const int fun(const int y)
> 
>{
> 
>// y = 9; ==>error
> 
>return y;
> 
>}
> 
>int main(){
> 
>int x = 20;
> 
>const int z = 10;
> 
>cout << fun(x) << '\n' << fun(z);
> 
>return 0;
> 
>}
 
(output= 20
 
10)

 ___________________________________________________________

 
**& uses in C++**

 
1-address operator

-unary operator that returns address of it's operand
 
example:

>int y=5;
>
>int*yptr=&y;
>
>//it store address (y) in pointer yptr
 
 
2-passing argument by reference

example:

>void CubeByReference(int*nptr){
>
>*nptr=*nptr**nptr**nptr;
>
>}
 
>void main(void){
> 
>int num =5;
>
>CubeByReference(&num);
>
>cout<<num;
>
>}

 
3-logic & (&&)

-returns true if both statements are true

>int  main(){
>
>int x=5;
>
>int y=3;
>
>cout<<(x>3 && x<10);
>                      
>return 0;
>
>}
                     
(output=1)

 
4-Bitwise operators in c++

>int main (){
>
>int a =5;
>
>int b=9;
>
>cout<<"a= " << a<<" , "<<"b="<<b<<endl;
>
>cout<<"a&b= "<< (a&b)<<endl;
>
>}
 
 
(output= a= 5 , b=9
                            
a&b= 1)
