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

## Inheritance (繼承)

- 透過 extends 繼承原型（父類別），原型會將自身的 properties 賦予新類別。
- super 聯繫父子類別。

```tsx
class StudentII extends Student {

	public nowListCourse(): string {
		return `現在的課表: ${$super.listCourses()}`;
	}
}

const studentTwo = new StudentII('Eric', 'Lin', 22 , ['Angular']);

console.log(studentTwo.nowListCourse());//現在的課表: ['Angular'];
```

### 子類別中執行 super 等同於父類別的 constructor:

```tsx
class StudentII extends Student {

	public nowListCourse(): string {
		return `現在的課表: ${$super.listCourses()}`;
	}
}

const studentTwo = new StudentII('Eric', 'Lin', 22 , ['Angular']);

console.log(studentTwo.nowListCourse());//現在的課表: ['Angular'];
```

### 在子類別中執行的 super 等同於父類別的 constructor

如果父類別和子類別同時需要在 Constructor 定義的 Property ，就得使用 super 傳入父類別需要的值：

```tsx
class ColorClass{
    color: string;
    
    constructor(color: string){
        this.color = color;
    }

    public showColor(): string{
        return this.color;
    }
}

class VersionClass extends ColorClass{
    version: number;

    constructor(color: string, version: number){
        super(color); //共同需要在 constructor 定義的 property，使用 super 傳入父類別需要的值。
        this.version = version;
    }

    public changeColor(newColor: string){
        this.color = newColor;
    }

    public showColor(): string{
        return super.showColor();
    }
}

const newVersion = new VersionClass('Red', 3);
newVersion.changeColor('blue');
console.log(newVersion); //versionClass {color: "blue", version: 3}
console.log(newVersion.showColor());
//blue
```

## Static (靜態)

透過 static 宣告的東西只能透過 class 呼叫。

```tsx
class ColorClass{
    color: string;
   / *省略*/
		
		static getComment(): string{
			return 'this is color class';
		}
}

class VersionClass extends ColorClass{
    
	/ *省略*/

    static getComment(): string{
        return 'this is version class';
    }
}

const newVersion = new VersionClass('Red', 3);
console.log(ColorClass.getComment()); //僅能透過 class 呼叫
console.log(VersionClass.getComment());

newVersion.getComment(); //error
```

## Protected

只需要將 Private 改成 Protected ，子類別便能存取被保護的 Property 了，而在 Instance 中，仍然無法偷看到該 Property。

```tsx
class Parent{
    protected genealogy: string;

    constructor(){
        this.genealogy = 'family read only';
    }
}

const parentInstance = new Parent();

 parentInstance.genealogy; //外部無法呼叫

class Child extends Parent{
    public getGenealogy(): string{
        return this.genealogy;
    }
}

const childInstance = new Child();

console.log(childInstance.getGenealogy());

childInstance.genealogy; //錯誤，外部不能呼叫。
```