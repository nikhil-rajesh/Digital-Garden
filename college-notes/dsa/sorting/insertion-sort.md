# Insertion Sort

Insertion sort selects the element one by one and keeps them in their right place.

```cpp
void insertionSort(vector<int>& arr)
{
    for (int i = 0; i < arr.size() - 1; i++) {
        int min = arr[i];
        for (int j = i + 1; j < arr.size(); j++) {
            if (arr[j] < min)
                swap(arr[j], min);
        }
        swap(min, arr[i]);
    }
}
```

