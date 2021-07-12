# Union Types (聯合型別)

```tsx
let favNumber: number | string;

//allowed
favNumber = 5;
favNumber = 'five';

//error
favNumber = true;

/////////////////////////
//更多使用方法
let name: string | string[];
```