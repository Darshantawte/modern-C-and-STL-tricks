# modern-C-and-STL-tricks

## No more nested `min(x, min(y, ...))`
Use initializer list and `std::min` and `std::max` to make life easy
```cpp
small = min(x, min(y, min(z, k))); // the old way
small = min({x, y, z, k}); // life is easy
```

## JavaScript like Destructuring using Structured Binding in C++
```cpp
pair<int, int> cur = {1, 2};
auto [x, y] = cur;
// x is now 1, y is now 2
// no need of cur.first and cur.second

array<int, 3> arr = {1, 0, -1};
auto [a, b, c] = arr;
// a is now 1, b is now 0, c is now -1

### How debug macros work?
Straight to the point, I have often used the `debug` macro which stringifies the variable names and their values.

```cpp
#define deb(x) cout << #x << " " << x 
int ten = 10;
deb(ten); // prints "ten = 10"
```

## Avoid remebering datatype of varibles
```cpp
vector<pair<pair<int,int>,int>> Job;


//traditonal way to travere
vector<pair<pair<int,int>,int>>:: iterator it;
for (it = Job.begin(); it < Job.end(); it++)
        cout << it->first->first << " "<<it->first->second<<" "....;


//cool way using - auto keyword which automatically identifies the datatype used

for(auto it:Job)
{
   cout<<it.first.first<<" "<<it.first.second<<" "<<it.second<<endl;
}
