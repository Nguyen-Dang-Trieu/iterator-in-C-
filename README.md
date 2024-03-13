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
