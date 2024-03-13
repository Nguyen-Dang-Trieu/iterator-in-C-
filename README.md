# iterator-in-C++

**Conference:** https://www.geeksforgeeks.org/iterators-c-stl/

**Khái niệm:**
Các iterator cho phép bạn duyệt qua các phần tử của một dãy dữ liệu mà không cần biết chi tiết về cách dữ liệu được tổ chức bên trong. Điều này làm cho mã của bạn trở nên linh hoạt hơn vì bạn không phụ thuộc vào cụ thể của cấu trúc dữ liệu mà bạn đang làm việc.

**Ví dụ:** Bạn có thể viết một hàm để tính tổng của tất cả các phần tử trong một dãy dữ liệu mà không cần biết liệu dãy dữ liệu đó có phải là một mảng, vector, list, hay bất kỳ cấu trúc dữ liệu nào khác. Bằng cách sử dụng iterator, bạn có thể truy cập vào từng phần tử của dãy một cách tổng quát mà không cần phải quan tâm đến cấu trúc cụ thể của dãy dữ liệu.

## 1. begin() - end()
~~~cpp
#include<iostream> 
#include<iterator> // for iterators 
#include<vector>   // for vectors 
using namespace std; 
int main() 
{ 
    vector<int> ar = { 7, 11, 45, 23, 19 };
      
    // ---- Declaring iterator to a vector ------
    /* Ta hiểu như này:
     index  0  1   2   3   4 
      ar =  7  11  45  23  19  (0)
            ^                   ^
            |                   |
        ar.begin()           ar.end()
    */
    // Cách 1:
    vector<int>::iterator ptr1 = ar.begin();
    
    /* Cách 2:
    vector<int>::iterator ptr1;
    ptr1 = ar.begin(); */
      
    vector<int>::iterator ptr2 = ar.end(); 
    vector<int>::iterator ptr3 = ar.begin(); 
      
      
    // Displaying vector elements using begin() and end() 
    cout << "Phần tử first của vector: " << *ptr1 << endl;
    cout << "Phần tử end của vector: " << *ptr2 << endl; 
    
    cout << "The vector elements are : "; 
    for (ptr3 = ar.begin(); ptr3 < ar.end(); ptr3++) 
        cout << *ptr3 << " "; 
      
    return 0;     
} 
~~~
Output:
~~~cpp
Phần tử first của vector: 7
Phần tử end của vector: 0
The vector elements are: 7 11 45 23 19
~~~

## 2.  advance()
This function is used to *increment the iterator position till the specified number mentioned in its arguments*.
~~~cpp
#include<iostream> 
#include<iterator> // for iterators 
#include<vector>   // for vectors 
using namespace std; 
int main() 
{ 
    vector<int> ar = { 7, 11, 45, 23, 19 }; 
      
    // Declaring iterator to a vector
    /*
     index  0  1   2   3   4 
      ar =  7  11  45  23  19  (0)
            ^                   ^
            |                   |
        ar.begin()           ar.end()           */
    vector<int>::iterator ptr = ar.begin(); 
      
    // ------ Using advance() to increment iterator position ---------
    
    // advance(iterator, số lần di chuyển)
    advance(ptr, 3);  // + số dương: di chuyển tới 
    // Displaying iterator position 
    cout << "The position of iterator after advance(ptr, 3) is : " << *ptr << endl;
    
    advance(ptr,-2);  // - số âm: di chuyển lùi
    // Displaying iterator position 
    cout << "The position of iterator after advance(ptr,-2) is : " << *ptr << endl;
       
    return 0; 
} 
~~~
Output:
~~~cpp
The position of iterator after advance(ptr, 3) is: 23
The position of iterator after advance(ptr,-2) is: 11
~~~

## 3. next() - prev()
~~~cpp
#include<iostream> 
#include<iterator> // for iterators 
#include<vector>   // for vectors 
using namespace std; 
int main() 
{ 
    vector<int> ar = { 7, 11, 45, 23, 19 };
      
    // Declaring iterators to a vector 
    vector<int>::iterator ptr = ar.begin(); 
    vector<int>::iterator ftr = ar.end(); 
     
     
    // Using next() to return new iterator 
    auto it = next(ptr, 0);  // next(iterator, số lần di chuyển)
    it = next(ptr,1);
      
    // Using prev() to return new iterator 
    auto it1 = prev(ftr, 3);  // prev(iterator, số lần di chuyển)
      
    // Displaying iterator position 
    cout << "The position of new iterator using next() is : " << *it << endl;

      
    // Displaying iterator position 
    cout << "The position of new iterator using prev()  is : " << *it1 << endl; 
      
    return 0;  
} 
~~~
Output:
~~~cpp
The position of new iterator using next() is: 11
The position of new iterator using prev() is: 45
~~~

## 4 - insert()
~~~cpp
#include<iostream>
#include<iterator>
#include<vector>
using namespace std;

int main()
{
    vector<int> ar = { 7, 11, 45, 23, 19 };
    vector<int>::iterator ptr = ar.begin(); // iterator pointing to the beginning of ar

    // Sử dụng advance để di chuyển iterator ptr đến vị trí muốn chèn
    advance(ptr, 3);

    // Chèn phần tử 100 vào vector ar sau vị trí mà iterator ptr đang trỏ đến
    ar.insert(ptr, 100);

    // In ra vector sau khi chèn
    cout << "Vector sau khi chèn phần tử 100 là: ";
    for (int &x : ar)
        cout << x << " ";

    return 0;
}
~~~
Output:
~~~cpp
Vector sau khi chèn phần tử 100 là: 7 11 45 100 23 19
~~~
