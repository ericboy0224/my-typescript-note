# Interface (介面)

## Interface 可以定義一個抽象的物件型別，跟 type aliases(型別別名) 一樣。

```tsx
interface Human{
	name: string;
	age: number;
	//定義物件要有一個 method 但先不定義函數內容。
	greet: () => void;
}
```

```tsx
type Human = {
	name: string;
	age: number;
//定義物件要有一個 method 但先不定義函數內容。
	greet: () => void;
}
```

```tsx
let Eric: Human;

Eric = {
	name: 'Eric',
	age: 22,
	greet(){
		console.log('Hello!');
	}
};

```

## Interface 獨有的 feature

Interface 多了一項 type aliases 沒有的功能，就是令 classes(類別) 執行 Interface 的型別。

```tsx
class Instructor implements Human {
	name: string;
	age: number;
	
	greet(){
		console.log('Hello');
	}
}
```