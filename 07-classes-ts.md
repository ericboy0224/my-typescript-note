# Classes & TS

## Class 就像是一張設計圖，能夠過它產生一個新物件。

```tsx
class Student {
	firstName: string;
	lastName: string;
	age: number;
	courses: string[];
	
	//建構子：傳入即時參數
	constructor(first: string, last: string, age: number, courses: string[]){
		this.firstName = first;
		this.lastName = last;
		this.age = age;
		this.courses = courses;
	}

	enrol(courseName: string){
		this.courses.push(courseName);
	}
}
// 生產新物件
const student = new Student('Eric', 'Lin', 22, ['Angular']);
student.enrol('TypeScript'); // student.courses => Angular, TypeScript
```

## Public & Private

- Public: class 外部可以取用的。
- Private: class 內部才能取用。

```tsx
class Student {
	public firstName: string;
	public lastName: string;
	public age: number;
	private courses: string[];
	
	//建構子：傳入即時參數
	constructor(first: string, last: string, age: number, courses: string[] ){
		this.firstName = first;
		this.lastName = last;
		this.age = age;
		this.courses = courses;
	}

	public enrol(courseName: string){
		this.courses.push(courseName);
	}

	public listCourses() {
		return this.courses.splice();
	}
}
// 生產新物件
const student = new Student('Eric', 'Lin', 22, ['Angular']);
student.enrol('TypeScript'); // student.courses => Angular, TypeScript

//因為 courses 是 private 我們只能透過呼叫 public 函式 student.listCourses();

```

## Shorthand

```tsx
class Student {
	
	//建構子：傳入即時參數
	constructor( public firstName: string, 
			public lastName: string, 
			public age: number, 
			private courses: string[] 
	){}

	public enrol(courseName: string){
		this.courses.push(courseName);
	}

	public listCourses() {
		return this.courses.splice();
	}
}
// 生產新物件
const student = new Student('Eric', 'Lin', 22, ['Angular']);
student.enrol('TypeScript'); // student.courses => Angular, TypeScript

//因為 courses 是 private 我們只能透過呼叫 public 函式 student.listCourses();

```