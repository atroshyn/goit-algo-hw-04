def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2
        L = arr[:mid]
        R = arr[mid:]

        merge_sort(L)
        merge_sort(R)

        i = j = k = 0
        while i < len(L) and j < len(R):
            if L[i] < R[j]:
                arr[k] = L[i]
                i += 1
            else:
                arr[k] = R[j]
                j += 1
            k += 1

        while i < len(L):
            arr[k] = L[i]
            i += 1
            k += 1

        while j < len(R):
            arr[k] = R[j]
            j += 1
            k += 1

          
def insertion_sort(arr):
    for i in range(1, len(arr)):
        key = arr[i]
        j = i - 1
        while j >= 0 and key < arr[j]:
            arr[j + 1] = arr[j]
            j -= 1
        arr[j + 1] = key

      
# Використовуємо вбудовану функцію sorted для Timsort
def timsort(arr):
    return sorted(arr)


import timeit
import random

# Генерація випадкового масиву
def generate_random_array(size):
    return [random.randint(0, 10000) for _ in range(size)]

# Вимірювання часу виконання кожного алгоритму на заданому масиві
def measure_time(algorithm, array):
    setup_code = f"from __main__ import {algorithm.__name__}, array"
    test_code = f"{algorithm.__name__}(array)"
    times = timeit.repeat(setup=setup_code, stmt=test_code, repeat=3, number=1)
    return min(times)

# Розміри масивів для тестування
sizes = [100, 1000, 5000, 10000, 20000]

# Результати
results = {}

for size in sizes:
    array = generate_random_array(size)
    array_copy1 = array.copy()
    array_copy2 = array.copy()
    array_copy3 = array.copy()

    time_merge_sort = measure_time(merge_sort, array_copy1)
    time_insertion_sort = measure_time(insertion_sort, array_copy2)
    time_timsort = measure_time(timsort, array_copy3)

    results[size] = {
        "Merge Sort": time_merge_sort,
        "Insertion Sort": time_insertion_sort,
        "Timsort": time_timsort
    }

# Виведення результатів
for size in sizes:
    print(f"Array Size: {size}")
    for algorithm in results[size]:
        print(f"{algorithm}: {results[size][algorithm]:.6f} seconds")
    print()
