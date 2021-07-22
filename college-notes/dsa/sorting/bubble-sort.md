# Bubble Sort

Bubble Sort works by repeatedly swapping the adjacent elements if they are in wrong order.

{% code title="bubbleSort.cpp" %}
```cpp
void bubbleSort(vector<int>& arr)
{
    for (auto i = arr.size() - 1; i != 0; i--) {
        for (auto j = 0; j != i; j++) {
            if (arr[j] > arr[j + 1]) {
                swap(arr[j], arr[j + 1]);
            }
        }
    }
}
```
{% endcode %}



