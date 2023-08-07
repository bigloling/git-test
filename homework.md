<p align='right'>< TeachMeSkills /></p>
<h1 align='center'>Functions</h1>

## Complete exercise

### NORMAL level

#### Task 1 💻

Написать функцию **getSum**, которая будет высчитывать сумму чисел от нуля, до параметра, который мы в неё передаем. 

> Если передадим число 100 то, надо вычислить сумму чисел от 0 до 100 (должно получится 5050)

#### Solution

```javascript
function getSum(num) {
    let result = 0

    for (; num >= 1; num--) result += num

    return result
}
```



#### Task 2 💻

Напишите функцию которая в качестве аргумента принимает в себя сумму кредита который хочет получить клиент и верните результат переплаты по кредиту:

+ процентная ставка в год — 17%,
+ количество лет — 5.

> Мы пишем функцию для хорошего банка, поэтому сумма кредита не увеличивается.

#### Solution

```javascript
let overPayment = (creditSum) => creditSum * 0.17 * 5
```



#### Task 3 💻

Написать функцию **`getSum`** которая принимает два целых числа a и b, которые могут быть положительными или отрицательными, найти сумму всех чисел между ними, включая их, и вернуть ее. Если два числа равны, верните a или b.

```javascript
    getSum(1, 0) == 1   // 1 + 0 = 1
    getSum(1, 2) == 3   // 1 + 2 = 3
    getSum(0, 1) == 1   // 0 + 1 = 1
    getSum(1, 1) == 1   // 1 Since both are same
    getSum(-1, 0) == -1 // -1 + 0 = -1
    getSum(-1, 2) == 2  // -1 + 0 + 1 + 2 = 2
```

#### Solution

```javascript
function getSum(a, b) {
    let res = 0
    let min, max

    if (a > b) { max = a; min = b }
    else if (a < b) { max = b; min = a }
    else return a

    for (min; min <= max; min++) {
        res += min
    }

    return res
}
```



#### Task 4 💻

Напишите функцию **fooboo** которая принимает в качестве аргумента три параметра:

+ булевое значение
+ функцию **foo** которая выводит в консоль 'foo'
+ функцию **boo** которая выводит в консоль 'boo'

> Если переданное булевое значение **true** запускаем функцию **foo** иначе **boo**

#### Solution

```javascript
let foo = () => console.log('foo')
let boo = () => console.log('boo')

let fooboo = (bool, funFoo, funBoo) => bool ? funFoo() : funBoo()
```



#### Task 5 💻

Напишите функцию **withNumberArgs()**, которая будет декорировать любую функцию
от двух переменных, которую вы в неё передадите.

Декорированная функция должна выводить в консоль ошибку, если тип одного из аргументов
не равен числу, и возвращать `0`:

```javascript
const mul = (a, b) => a * b;

const safeMul = withNumberArgs(mul);

safeMul(5, 5) // 25
safeMul(5, "5") // 0, ошибка в консоли - неверный тип параметра
```

#### Solution

```javascript
const mul = (a, b) => a * b

function withNumberArgs(func) {
    return function(a, b) {
        return typeof(a) == 'string' || typeof(b) == 'string' ? 0 : func(a, b)
    }
}

const safeMul = withNumberArgs(mul)

safeMul(5, 5)
safeMul(5, "5")
```



### ADVANCED level

#### Task 1 👨‍🏫 

+ Реализуйте функцию, который принимает 3 целочисленных значения a, b, c. Функция должна возвращать **true**, если треугольник можно построить со сторонами заданной длины, и **false** в любом другом случае.

#### Solution

```javascript
function triangle(a, b, c) {
    let max = Math.max(a, b, c)
    return max < a + b + c - max ? true : false
}
```



#### Task 2 👨‍🏫

+ Напишите программу для вычисления общей стоимости покупки телефонов. Вы будете продолжать покупать телефоны (подсказка: циклы!), пока у вас не закончатся деньги на банковском счете. Вы также будете покупать аксессуары для каждого из телефонов.

+ После того, как вы посчитаете сумму покупки, прибавьте налог, затем выведите на экран вычисленную сумму покупки, правильно отформатировав её.

+ Наконец, сверьте сумму с балансом вашего банковского счета, чтобы понять можете вы себе это позволить или нет.

+ Вы должны настроить некоторые константы для «ставки налога», «цены телефона», «цены аксессуара», также как и переменную для вашего «баланса банковского счета».

+ Вам следует определить функции для вычисления налога и для форматирования цены со знаком валюты и округлением до двух знаков после запятой.

+ Как последний этап, попробуйте включить ввод данных в вашу программу, например с помощью функции prompt(..). Вы можете, например, запросить у пользователя баланс банковского счета. Развлекайтесь и будьте изобретательны!

#### Solution

```javascript
const balance = prompt("Enter your bank account balance:")

const phoneCost = 2000
const headphonesCost = 400
const powerBankCost = 100
const phoneChargerCost = 50
const tax = balance * 0.13
let purchaseAmount = 0


function purchase(balance) {
    let resultBalance = balance

    while(resultBalance > 0) {
        let choice = prompt(`Your balance: ${resultBalance}. With tax: ${resultBalance - tax}\nSelect products:\n1. Phone - 2000\n2. Headphones - 400\n3. Power bank - 100\n4. Phone charger - 50\n5. Stop selecting`)
        if (choice === '5') break;
        else {
            switch (choice) {
                case '1':
                    purchaseAmount += phoneCost
                    resultBalance -= phoneCost
                    alert("Item added")
                    break;
                case '2':
                    purchaseAmount += headphonesCost
                    resultBalance -= headphonesCost
                    alert("Item added")
                    break;
                case '3':
                    purchaseAmount += powerBankCost
                    resultBalance -= powerBankCost
                    alert("Item added")
                    break;
                case '4':
                    purchaseAmount += phoneChargerCost
                    resultBalance -= phoneChargerCost
                    alert("Item added")
                    break;
                default:
                    alert("Invalid input")
                    break;
            }
        }
    }


    alert(`Purchase amount (with tax): ${purchaseAmount + tax}\nYour balance: ${balance}`)
    
    if(balance - tax < purchaseAmount) alert("Not enough money to buy")
    else alert("Purchase successful")
}

purchase(balance)
```



#### Task 3 👨‍🏫 - дополнительно

+ Ваша задача - разбить плитку шоколада заданного размера n x m на маленькие квадраты. Каждый квадрат имеет размер 1x1 и не может быть разбит. Реализуйте функцию, которая будет возвращать минимальное количество необходимых надломов.

+ Например, если вам дается плитка шоколада размером 2 x 1, вы можете разделить ее на отдельные квадраты всего за один надлом, но для размера 3 x 1 вы должны сделать два надлома.

+ Если входные данные недействительны, вы должны вернуть 0 (поскольку надломы не требуются, если у нас нет шоколада для разделения). Ввод всегда будет неотрицательным целым числом.

#### Solution

```javascript
let m = prompt("Enter the Length of the chocolate bar:")
let n = prompt("Enter the Width of the chocolate bar:")

function splitting(m, n) {
    while (m < 1 || n < 1 || m % 1 !== 0 || n % 1 !== 0) {
        alert("Invalid input. Try again")
        m = prompt("Enter the Length of the chocolate bar:")
        n = prompt("Enter the Width of the chocolate bar:")
    }

    alert(`Minimum number of fractures for a chocolate bar of size ${m} x ${n}: ${Number(m) + Number(n) - 2}`)
}

splitting(m, n)
```