//# quick-sort-in-cpp-using-recursion-
//quick sort in cpp using recursion 

#include <bits/stdc++.h>
using namespace std;

int pivot(int arr[], int s, int e){
    int pivotelement = arr[s];
    int count = 0;
    for(int i =s+1; i<=e; i++ ){
        if(arr[i] <= pivotelement){
            count++;
        }
    }
    
    int pivotindex = s+count;
    swap(arr[s], arr[pivotindex]);
    
    int i =s;
    int j =e;
    while(i<pivotindex && j>pivotindex){
        while(arr[i] < pivotelement){
            i++;
        }
        
        while(arr[j] > pivotelement){
            j--;
        }
        
        if(i<pivotindex && j> pivotindex){
            swap(arr[i] , arr[j]);
            i++;
            j++;
        }
    }
    return pivotindex;
}

void qs(int arr[], int s, int e){
    // base case
    
    if(s>=e){
        return ;
    }
    
    int p = pivot(arr, s, e);
    
    qs(arr, s, p-1);
    qs(arr, p+1, e);
    
}

void quicksort(int arr[] , int size){
    qs(arr, 0, size -1);
}

int main()
{
    int n;
    cin >>n;
    int *arr = new int[n];
    for(int i =0; i<n; i++){
        cin >> arr[i];
    }
    
    for(int i =0; i<n; i++){
        cout<< arr[i] << " ";
    }cout<< endl;
    
    quicksort(arr, n);
    
    cout<<"After Sorting" << endl;
    
    for(int i =0; i<n; i++){
        cout<< arr[i] << " ";
    }cout<< endl;
    

    return 0;
}

