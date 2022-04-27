```C++
void example1(){
    vector<int> v;
    v.push_back(0);
    int* src = &v[0];
    v.resize(10000000);
    cout << &v[0] << " " << src;
    /*
     * 0x2676040 0x7b1750
     * */
}
```

```c++
void example2(){
    vector<int> v;
    v.push_back(0);
    int& src = v[0];
    v.resize(10000000);
    v[0] = 2;
    cout << v[0] << " " << src << endl;
    /*
     * 2 8068784
     * */
}
```

