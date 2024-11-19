def quicksort(n, low, high):
    if low < high:
        # Partition the array and get the pivot index
        p = partition(n, low, high)
        # Recursively apply quicksort to the left and right partitions
        quicksort(n, low, p - 1)
        quicksort(n, p + 1, high)

def partition(n, low, high):
    pivot = n[low]  # Choose the first element as the pivot
    left = low + 1
    right = high

    while left <= right:
        # Find the first element greater than the pivot
        while left <= right and n[left] <= pivot:
            left += 1
        # Find the first element smaller than the pivot
        while left <= right and n[right] > pivot:
            right -= 1
        # Swap out-of-place elements
        if left < right:
            n[left], n[right] = n[right], n[left]

    # Place the pivot in its correct position
    n[low], n[right] = n[right], n[low]
    return right

# Example usage
n = [12, 4, 3, 5, 2, 6, 5]
quicksort(n, 0, len(n) - 1)
print("Sorted Array:", n)
