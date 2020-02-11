# Doing pug-examples

## _Following this article :_

><https://www.sitepoint.com/a-beginners-guide-to-pug/>

---

### _Some basic rules and syntax :_

**1._Pug doesn't have any closing tags_**

2.```.rermark``` = ```div.remark```

```html
 <div class="remark">
 </div>
```

3._Classes, IDs_

```pug
 nav#navbar-default
  .container-fluid
   h1.navbar-header heading
```

 _equivent to_ :

```html
<nav id="navbar-default">
  <div class="container-fluid">
    <h1 class="navbar-header">heading</h1>
  </div>
</nav>
```

4._Attributes are added using brackets_

```pug
input(
  type='text'
  name='search'
  placeholder='Enter a search term'
)
```

 _equivent to_ :

```html
<input type="text" name="search" placeholder="Enter a search term..."/>
```

5._Plain text and text blocks_

- Plain text: 2 ways

```pug
h1.navbar-header My Website! We can write anything we want here …
```

```pug
h1.navbar-header
 | My Website!
 | We can write anything we want here …
```

- Text blocks

```pug
p.
 Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry's standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.
 ```

6._Comments_

- **Note** : Comments must appear on their own line

```pug
// This is a comment

//- Also a comment but remain in pug file

//
 Multiline comments
 comment 1
 comment 2
 ...
 ```

**7._JavaScript in Pug_**

- Unbuffered code : start with a minus (-)

```pug
- const name = "Jim"
//- Now I can refer to a 'name' variable in my Pug code
```

- Buffered code : start with an equal (=)

```pug
p= 'Two to the power of ten is: ' + 2**10
```

_// equivent to_

```html
<p>
  Two to the power of ten is: 1024
</p>
```

 _For reasons of security, buffered code is HTML escaped :_

```pug
p= '<script>alert("Hi")</script>'
```

8._Interpolation_

```pug
- const name = 'jim'
p Hi #{name}

//Brackets can contain any valid JS expression, this opens up a bunch of possibilities
p Hello #{name.charAt(0).toUpperCase() + name.slice(1)}
```

// compile to

```html
<p>Hi jim</p>

<p>Hello Jim</p>
```

- **Note**: when you want to assign the value held in a variable to an element’s attribute, you can omit the #{}. For example: img(alt=name).

9._Iteration_:

- **Note**: `each` keyword makes it easy to iterate over arrays

```pug
- const employees = ['Angela','Jim','Nilson','Simone']
ul
 each employee in employees
  li= employee

-
 const employee_1 = {
   'First Name': 'James',
   'Last Name': 'Hibbard'
 }
ol
 each value, key in employee_1
  li= `${key} : ${value}`

- const employees_2 = []
 ul
  each employee in employees_2
   li= employee
   else
   li The company doesn't have any employees. Maybe hire some?
```

//compile to

```html
<ul>
  <li>Angela</li>
  <li>Jim</li>
  <li>Nilson</li>
  <li>Simone</li>
</ul>

<ol>
  <li>First Name: James</li>
  <li>Last Name: Hibbard</li>
</ol>

<ul>
  <li>
    The company doesn't have any employees. Maybe hire some?
  </li>
</ul>
```

10._Conditionals_

```pug
-
 const employee = {
   firstName: 'James',
   lastName: 'Hibbard,
   extn: '12345'
 }

#employee
 p= `${employee.firstName} ${employee.lastName}`
 p Extension :
  if employee.extn
   =employee.extn
  else
   | n/a
```

//compile to

```html
<p>
  James Hibbard
</p>
<p>
  Extension: 12345
</p>
```
