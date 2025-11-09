
```c
#include<stdio.h>

void bubbleSort(int arr[],int n){
    int temp;
    // Traverse through all array elements
    for (int i=0;i<n-1;i++){
        for(int j=0;j<n-1;j++){
            if(arr[j]>arr[j+1]){
                temp=arr[j];
                arr[j]=arr[j+1];
                arr[j+1]=temp;
                
                
            }
        }
    }
}
void printArray(int arr[],int size){
    for(int i=0;i<size;i++){
        printf("%d",arr[i]);
        
    }
    printf("\n\n");
}
int main(){
    int arr[]={3,4,6,7,2,1,8,0};
    int n=sizeof(arr)/sizeof(arr[0]);
    printf("original array:\n\n");
    printArray(arr,n);
    bubbleSort(arr,n);
    printArray(arr,n);
    return 0;
}

```


```c
#include<stdio.h>
void selectionSort(int arr[],int n)
{
int minIndex,temp;
//Traverse the array
for (int i=0;i<n-1;i++){
	minIndex=i;
	for(int j=i+1;j<n;j++){
	if(arr[j]<arr[minIndex]){
		minIndex=j;
		
	}
	}
	if(minIndex!=i){
	temp=arr[i];
	arr[i]=arr[minIndex];
	arr[minIndex]=temp;
	
	}
}
}
void printArray(int arr[],int size){

	for(int i=0;i<size;i++){
	print
	}

}

int main(){

int arr[]={64,25,12,22,11};
int n=sizeof(arr)/sizeof(arr[0]);
printf("Original array:\n");
printArray(arr,n);
selectionSort(arr,n);
printf("Sorted array:\n");
printArray(arr,n);

}
// i changes shit hereee ok
```


Concept:Builds Stored list one element at a time b

2.Shift element to the right to create space for insertion.
3.insert the element in the correct position.
Example(Sortiong[5,3,8,4,2]):




