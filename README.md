# quick-sort
#include <stdio.h>

void swap(int* a, int* b) {
    int t = *a;
    *a = *b;
    *b = t;
}

int Partition(int A[], int lb, int Ub) {
    int Pivot = A[lb];
    int start = lb;
    int end = Ub;

    while (start < end) {
        while (A[start] <= Pivot) {
            start++;
        }
        while (A[end] > Pivot) {
            end--;
        }
        if (start < end) {
            swap(&A[start], &A[end]);
        }
    }
    swap(&A[lb], &A[end]);
    return end;
}

void QuickSort(int A[], int lb, int Ub) {
    if (lb < Ub) {
        int loc = Partition(A, lb, Ub);
        QuickSort(A, lb, loc - 1);
        QuickSort(A, loc + 1, Ub);
    }
}

void printArray(int A[], int size) {
    for (int i = 0; i < size; i++) {
        printf("%d ", A[i]);
    }
    printf("\n");
}

int main() {
    int n;
    printf("Enter the number of elements: ");
    scanf("%d", &n);

    int arr[n];
    printf("Enter %d elements:\n", n);
    for (int i = 0; i < n; i++) {
        scanf("%d", &arr[i]);
    }

    printf("Original array: \n");
    printArray(arr, n);

    QuickSort(arr, 0, n - 1);

    printf("Sorted array: \n");
    printArray(arr, n);

    return 0;
}

