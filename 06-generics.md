# Generics (泛型)

## 

## ❌(非泛型)

缺點是沒有在精確的型別下回傳值... 

```tsx
function insertAtBeginning (array: any[], value: any){
	const newArray: = [value, ...array];
	return newArray;
}
```

## ⭕️(泛型)

在定義函式、介面或類別時，不預先預設值，使用再指定。

- 在函式後面加上 <T> ，T用來指代任意輸入型別

```tsx
function insertAtBeginning<T> (array: T[], value: T){
	const newArray: = [value, ...array];
	return newArray;
}
```