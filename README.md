# 정렬

: 각 정렬방법들의 성능비교는 마지막에 있습니다.

## 버블정렬(Bubble Sort)

:두 개의 인접한 원소를 비교하여 정렬하는 방식.


### 방법

1. 앞에서부터(인덱스 숫자가 작은) 현재 요소와 다음 요소를 비교.
2. 현재 요소가 다음 위치의 요소보다 크다면, 요소 교환.
3. 다음 요소로 이동하여 해당 요소와 그 다음 요소를 비교.


### 소스코드

	package BubbleSort;

	public class BubbleSort {
		public static void BSort(int[] a) {
			BSort(a,a.length);
		}
		private static void swap(int[]a,int i,int j) {
			int temp = a[i];
			a[i]=a[j];
			a[j]=temp;
		}
		private static void BSort(int[]a,int size) {
		
			for(int i=1;i<size;i++) {
				for(int j=0;j<size-i;j++) {
					if(a[j]>a[j+1]) {
						swap(a,j,j+1);
					}
				}
			}
		}
	}

### 시간복잡도

* 최선의 경우: O(n)

* 최악의 경우: O(n^2)

* 평균: O(n^2)

## 선택정렬(Selection Sort)

:현재 위치에 들어갈 데이터를 찾아 선택하는 방식.

데이터를 비교하면서 찾기 때문에 비교정렬 이라고도 한다.


### 방법

1. 주어진 리스트 안에서 최소값을 찾기.
2. 최소값을 맨 앞자리의 값과 교환.
3. 맨 앞자리를 제외한 나머지 값 중, 최소값을 찾아 계속 반복한다.


### 소스코드

	package SelectionSort;

	public class SelecSort {
		public void sort(int[] a) {
			int size=a.length;
			int min,temp;
		
			for(int i=0;i<size-1;i++) {
				min=i;
				for(int j=i+1;j<size;j++) {
					if(a[min]>a[j]) {
						min=j;
					}
			
					temp=a[min];
					a[min]=a[i];
					a[i]=temp;
				}
			}
		}

		public static void main(String[]args) {
			SelecSort selec = new SelecSort();
			int n[]= {4,3,1,5,2};
		
			selec.sort(n);
		
			for(int i=0;i<n.length;i++) {
				System.out.print(n[i]);
			}
		}
	}

### 시간복잡도

* 최선의 경우: O(n^2)

* 최악의 경우: O(n^2)

* 평균: O(n^2)


## 삽입정렬

:현재 비교하고자 하는 타겟 요소와 그 전의 요소들을 비교하며 자리를 교환하는 방식.

### 방법

1. 현재 타겟이 되는 요소와 이전 위치의 요소들을 비교.(첫번째 타겟은 두번째 요소부터 시작)
2. 타겟이 되는 요소가 이전 위치에 있던 요소보다 작으면 위치를 교환.
3. 다음 타겟 요소를 찾아 계속 반복.

### 소스코드

	package InsertionSort;
	
	import java.util.Scanner;
	
	public class InsertionSort {
		public static void printSort(int[]a) {
			for(int i=0;i<a.length;i++) {
				System.out.print(a[i] );
			}
		}
		public static void main(String[]args) {
			int[] a= {5,1,3,2,4};
			
			for(int i=1;i<a.length;i++) {
				int j=a[i];
				int k=i-1;
				
				while (k >=0 && j<a[k]) {
					a[k+1]=a[k];
					k--;
				}
				a[k+1]=j; //기준값 저장
			}
			printSort(a);
		}
		
	}


### 시간복잡도

* 최선의 경우: O(n)

* 최악의 경우: O(n^2)

* 평균 : O(n^2)


## 쉘 정렬

: 요소들을 그룹으로 나눠 그룹별 단순 삽입정렬 수행하고 그룹들을 합치며 정렬 반복, 요소의 이동 횟수를 줄이는 

### 방법

1. 간격별로 분류된 부분 리스트에 대해 삽입정렬 수행.
2. 부분 리스트의 정렬이 끝나면 간격 줄이기.
3. 간격이 1이 될 때 까지 2~4 반복.

### 소스코드

	package ShellSort;

	public class ShellSort {
		public static void main(String[] args) {
			int[]a= {5,1,4,2,3};
			int n=a.length;
			
			for(int g=n/2; g>0;g/=2) {
				for(int i=g;i<n;i++) {
					int j;
					int temp=a[i];
				
					for(j=i-g;j>=0 && a[j]>temp;j-=g) {
						a[j+g]=a[j];
					}
					a[j+g]=temp;
				}
			}
			for(int i=0;i<a.length;i++) {
				System.out.print(a[i]);
			}
		}
	}


### 시간복잡도

* 최악의 경우: O(n^2)
* 최선의 경우: O(n)
* 평균: O(n^1.5)


## 정렬별 시간복잡도와 안정성 비교


### <버블정렬>

-시간 복잡도 측면-

* 최선의 경우: O(n)

* 최악의 경우: O(n^2)

* 평균: O(n^2)


-안정성 측면-

* 안정정렬



### <선택정렬>

-시간 복잡도 측면-

* 최선의 경우: O(n^2)

* 최악의 경우: O(n^2)

* 평균: O(n^2)

-안정성 측면-

* 불안정정렬


### <삽입정렬>

-시간 복잡도 측면-

* 최선의 경우: O(n)

* 최악의 경우: O(n^2)

* 평균 : O(n^2)

-안정성 측면-

* 안정정렬


### <쉘 정렬>
	
-시간 복잡도 측면-
* 최악의 경우: O(n^2)
* 최선의 경우: O(n)
* 평균: O(n^1.5)

-안정성 측면-

* 불안정정렬





*쉘 정렬이 시간복잡도 측면에서 가장 우수하다.



