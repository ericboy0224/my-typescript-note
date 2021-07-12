# Function & Void

## Function

如下 TS 已經確定 function 回傳值為 number

```tsx
function add(a: number, b: number){
	return a+b;
}

//等同於

function add (a: number, b: number): number{
	return a+b;
}
```

### Void

Void 即代表無型別(null, undefined)，定義一個變數沒有意義。下列函式目前沒有回傳任何值。

```tsx
function print(value: any){
	console.log(value);
}

//等同於

function print() :void {}
```