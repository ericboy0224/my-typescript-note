# 宣告

## Primitives (原型類別)

```tsx
let age: number;
age = 22;

let name: string;
name = 'Eric'

let isInstructor: boolean;
isInstructor = false;

////////////////////////////////////

let age: number = 22;
let name: string = 'Eric';
let isInstructor: boolean = false;
```

## Arrays & Objects

```tsx
let hobbies: string[];  // 宣告陣列內僅能夠有 string type

//宣告物件＆內容物型別
let person: {
	name: string;
	age: number;
};

//未在宣告出現的會報錯
let person = {
	isTrue : true //Error
};

////////////////////////////
//ㄧ個陣列內有多個物件

let person: 
	name: string;
	age: number;
}[];

```

## 任意值(Default)

```tsx
let me: any; //不定義為何種型態

let she: any = 25;
she = 'Jane'; //不會顯示 Error

let hi; //沒有宣告型別預設就是 any
```

## 未宣告型別賦值

### 在宣告時直接賦值，會默認型別。

```tsx
let name = 'Eric'; //let name: string; 
name = 1; //Error
```