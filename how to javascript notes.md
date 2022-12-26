# Javascript Notes

# Javascript Grunder - Notes

Alert = Popup, (VB Msgbox) 
Alert(“Hello World!”)
“use strict”; >> upptäcker fler misstag.
inline script; ej behöva ladda in en annan fil, skrivs direkt i html filen.
&lt;script src=”script.js”>&lt;/script> för att länka en html till till js, brukar göra detta i slutet på &lt;/body>

// för comments eller /* och */ för multiline.
**<span style="text-decoration:underline;">Variabler</span>**

## **<span style="text-decoration:underline;">Variabler</span>**
```
Let (vb dim), definering av variabel första gången.
let namn = “hello”
Om man definierar om (variabler kan vara dynamiska) använder man ej let
Variabler i JS skrivs med camelcase = firstPersonName
Börja aldrig med nummer, kan bara innehålla number, letter, underscore och dollarsign
Börja alltid med lowercase, annars är det OOP. 
Variable kan vara primitiva eller object. **Alltid dynamiska!**
Primitiva är dom vanliga, 7st, number (heltal+decimal), “string”, bool, 
Undefined (Not yet defined, empty), Null, Symbol, BigInt
Använd typeof operator för att få resultatet av en variable.
console.log(typeof variableNamn);
**const** = värdet kan inte ändras.
Alla bokstäver i stora bokstäver = **constant**, ska aldrig ändras.
använd const så mycket som möjligt, mindre buggar.
**_var = gamla sättet att definiera let, använd ej._**
Alla variabler som definieras inne i ett kod-block, måste definieras utanför också - dom gäller bara inne i kodblocket.
**Iterable **are objects that can be iterated over with for..of
```

## **<span style="text-decoration:underline;">Strings</span>**

```
const plane = "Airbus A320 Neo"
plane[0]; //=A eller plane.at(0)  bra för method chaining
plane.length;
plane.indexOf('3') //= 8 - Kan även söka hela ord, case sensitive -1 om ej hitta.
plane.lastIndexOf('A'); // =7
cl = plane.slice(7); // A320, 7 är där den börjar
cl = plane.slice(7,11); // A320, 11 är slutar. Längd alltid end - start.
cl = plane.slice(0, plane.indexOf(' ')); = Airbus
cl = plane.slice(-3); >>> Neo, räknar från slutet
plane.toLowerCase();
plane.toUpperCase(); =  >>> AIRBUS A320 NEO
plane.trim(); =  >>> Tar bort space, tab, no-break space, etc.
plane.toLowerCase().trim(); >>> Kan köra flera - chaining
plane.replace('Neo', 'Shit'); //Bara första occurence
plane.replaceAll('Neo', 'Shit'); //Alla occurence
plane.includes('Neo'), .startsWith("Airbus"), .endsWith >>> True/False
plane.split(' '); >>> ["Airbus","A320","Neo"]
const [Company, Model, Future] = plane.split(' ');
const NewPlane = planeArray.join('---');  >> Joins array to string
plane.padStart(25,"+") / .padEnd(25,"+") >>> Adderar till längd
plane.padStart(2)  >>> Skapar ny sträng med 2 repeats
```



## **<span style="text-decoration:underline;">Numbers</span>**

**Numeric seperator (readability): _**


```
const solarSystemDiameter = 287_460_000_000;
```


**BigInt**

Kan få stora nummer, ex från databas ID eller APIs som behövs sparas.

Sätter ett n efter:


```
const bigNumber = 8723489327498732409273492n;
const bigNumber = BigInt(8723489327498732409273492);
```



## **<span style="text-decoration:underline;">Template Literals</span>** - 

används för att visa JS samt ${}


```
const description1 = `${country} is in ${continent}, and its ${population} million people speaks ${language}`;
```


Använd alltid ``för alla strings.

\n\ betyder ny line (används ej), med Tempalte literals använd bara enter för ny lines.


## Type conversion

**Numbers**

Göra om string till number; Number(string); (NaN om de inte är ett nummer)

Kan även göra +string för att konvertera den.


```
Number.parseInt('30 years old') > 30 > hitta numret, nr måste först
Number.parseFloat('5.6 years old') > 5.6 > Hitta float i string.
Number.isFinite(20) >>> True/False (Kan även använda NaN eller isInteger)


```


**Strings**

String() för att göra en string av ex nummer.

Boolean();

“String” + “String” = “StringString”

Falsy values = 0, “”, undefined, null, NaN        Truly values = Allt annat.

Konvertering av ovan till Bool vill resultera i false eller true.

Kan användas i IF = 0 = False


## Equality operators

=== båda sidorna lika innebär true, annars false

==, samma sak men ej lika strikt. Kan göra type conversion.(Använd ej!)

!== och (!=) är inte lika med


## And / OR

Boolean login >> And (&&), Or (||) + Not (!)

short-circuit: kan använda ALLA datatyper. Om försa värdet är truthy kommer det alltid retunera true.

Vid **OR ||**: Är första true, kommer andra inte ens bli kollad på.


```
console.log(3 || "Andreas");  >> 3
console.log(Undefined || "Andreas"); >> Andreas
const g = r.numGuests || 10; 
 >>> 0, "", Null och Undefined på r.NumGuests kommer göra g till 10.
```


Kan bli problem man har ett “true” value som är 0 (eftersom det är false).

_<span style="text-decoration:underline;">Nullish Coalescalong operator </span>_- här är bara null och undefined som är false


```
const g = r.numGuests ?? 10; 
   >> bara om r.numGuest = null eller undefined blir det 10.
```


**OR/Nullish		 **||= 	??=


```
 rest1.numGuests = rest1.numGuests || 10; (Om rest1.n inte finns, sätt 10)
 rest1.numGuests ||= 10;	bättre>>	 rest1.numGuests ??= 10;  
```


**And assignment operator**


```
rest1.owner = rest1.owner && '<ANONYMOUS>';
rest1.owner &&= '<ANONYMOUS>'; >> Om rest1.owner finns, byta ut till ""
```


Vid **AND &&**: Är första värdet false returneras detta utan att andra kollas på.


```
console.log(0 && Andreas);  >> 0
console.log(7 && Andreas);  >> Andreas
```


Kan användas istället för IF block (om man vill det ska stoppas på false)


```
r.orderPizza && r.orderPizza('mushrooms', 'spinach');
```


Om r.orderpizza finns (true) kommer funktionen efter && executas.


## Case

Alltid strict comparison (===)


```
let day = "Monday";
switch (day) {
    case "Monday":
        console.log(`It is ${day}`)
        break;
    case "thuseday":
        console.log(`It is ${day}`)
        break;
    default:
        console.log(`It is uknown day`)
}
```


Expression = value (Words)

Statement, not value (sentences) (Ex, If, else).

Javascript förväntar sig olika på olika ställen

**Conditional Operator (Ternary)**

condition ? vad som utförs om det är true : annars utförs detta


```
const age = 18;
age >= 18 ? console.log("Im old enough") : console.log("Im not old enough");
```


Kan vara ett expression:


```
const drink = age >= 18 ? "Yes" : "No";
```



## **<span style="text-decoration:underline;">Math</span>**


## Operator

Math, logical, comparison… 

Plus/Minus osv… ** = Power of, ex 2**3 = 2*2*2

**Assignment**; **=**  

X = 10+5

X += 10 lägger till 10. Plus kan bytas ut

X++ lägger till 1, x– drar ifrån en **(OBS: retur av prev value!) Kan ej göra var eller cl.**

++x - samma som ovan, men gör retur av nya värdet. 

**Comparison **&lt; > =>

Villken operator körs först = MDN operator preceadanse

**Math**


```
Math.sqrt(25) >>> Roten ur

Math.max(2, 35, 7, 8, 33) Min eller Max 
const numbers = [1, 2, 3, 4, 5, 6, 7];
console.log(Math.max(...numbers));

Math.random() > Ger ett random nr mellan 0 och 1 (Multiplicera + 1!)
const randomInt = (min, max) => Math.trunc(Math.random() * (max + 1 - min) + min);
const randomArray = Array.from({ length: 100 }, () => randomInt(1, 4));

Math.trunc(23.4); >>> Tar bort decimal
Math.round(23.1); Math.round(23.7); >> Avrundar till närmsta heltal
Math.ceil(number); Math.floor(number); Heltal upp/ner

+(2.356).toFixed(2) >>> 2.36 (avrundar till decimal) < +number.toFixed(2)
```


**Remainder ( % )**

Vid division, det som är kvar för heltal. Kan användas för att se odd/even


```
const isEven = n => n % 2 === 0;
console.log(isEven(7)); << False       console.log(isEven(8)); << True
```


Smart att använda om du behöver göra en sak varje X gång i en loop (Ex i % 3 === 0)


## Date & Time


```
const now = new Date();
console.log(now);  >>> 
Sun Nov 06 2022 20:49:45 GMT+0100 (centraleuropeisk normaltid)
```


Parse from string:


```
const parseDateFrString = new Date('November 16 2022'); (Unreliable!)
```


Parse date from Year, Month, Day, Hour, Minut, second


```
const parseDateFromDate = new Date(2022, 11, 16, 12, 0, 0);
```


OBS: Month = 0 based, så månad 11 innebär december.

Unixtime:


```
const unixTime = new Date(1667764654000);
```


**Operations**


```
const year = future.getFullYear();
const month = future.getMonth() + 1;
const day = future.getDate();
const dayofweek = future.getDay();  > 1-7
future.getHours();       future.getMinutes();        future.getSeconds();
const internationalStandard string = future.toISOString();
future.getTime(); /Unix timestamp
const now = Date.now(); /Unix timestamp
```


Finns set funktioner på alla ovan:


```
future.setFullYear(1987);
```


Date in the right format:


```
new Intl.DateTimeFormat(locale, options).format(theDate)
```


Usecase: (Date in user format)


```
const displayDate = function (
  newDate, // Input date in UNIX
  withTime = false, // Return formated date AND time?
  withTextforCloseDays = false // Return Today, Yesterday, X days ago for last week?
) {
  const theDate = new Date(newDate);
  const optionTime = {
    weekday: 'long',
    year: 'numeric',
    month: 'long',
    day: '2-digit',
    hour: '2-digit',
    minute: '2-digit',
    //Short, narrow, 2-digit, long, numeric
  };
  const optionDate = {
    weekday: 'long',
    year: 'numeric',
    month: 'long',
    day: '2-digit',
  };
  const localeUser = navigator.language;
  //en-GB, or other ISO language codes

  if (!withTextforCloseDays) {
    return withTime
      ? new Intl.DateTimeFormat(localeUser, optionTime).format(theDate)
      : new Intl.DateTimeFormat(localeUser, optionDate).format(theDate);
  } else {
    //Return tomorrow, today, yesterday.
    const DaysPassed = Math.round(
      Math.abs((newDate - new Date()) / (1000 * 60 * 60 * 24))
    );
    if (DaysPassed === 0) return 'Today';
    if (DaysPassed === 1) return 'Yesterday';
    if (DaysPassed <= 7) return `${DaysPassed} days ago`;
    else {
      return withTime
        ? new Intl.DateTimeFormat(localeUser, optionTime).format(theDate)
        : new Intl.DateTimeFormat(localeUser, optionDate).format(theDate);
    }}};
```


**Date calculations**

För att göra beräkningar, gör om värdet till Unix tid och beräkna ex mellanskillnaden, 


```
const calcDaysPassed = >> 1000ms * 60 sec * 60 min * 24h = dagar
Math.abs((date1 - date2) / (1000 * 60 * 60 * 24));
calcDaysPassed(new Date(2022, 4, 1), new Date(2022, 3, 1));
```


Finns bra biblioket (moment.js)

För att formatera nummer, ex currency eller procent


```
Intl.NumberFormat(locale, {option object}).format(number);
```



## Functions

Kod som man kan återanvända flera gånger.

function logger(argument, argument) { KOD }

Call/Invoke/run/execute: logger();

return variable;

**Default parameters (om en parameter saknas)**


```
const createBooking = function (flightNum, numPassangers = 1, price =-1){}
```


Det går också att göra beräkningar i parametrar (definierade efter den som kallas!)


```
const createBooking = function (flightNum, numPassangers = -1,
price = 199 * numPassangers) >>> Fortfarande bara "default" om det saknas
```


Vill man kalla med ett argument som man inte vet - undefined


```
createBooking('HEL666', undefined, 10);
```


**<span style="text-decoration:underline;">Olika funktioner</span>**

**Function:**

Kan användas innan deklarationen


```
function percentageOfWorld1(populationInMil) {
    return (populationInMil / 7900) * 100; }
console.log(percentageOfWorld1(1441));
```


**Function Expression:**

Value som blir stored i en variable.


```
const percentageOfWorld2 = function (populationInMil2) {
    return (populationInMil2 / 7900) * 100; }
console.log(percentageOfWorld1(1441));
```


**Arrow function:**

Ej return, {}, vid bara “one liner”. Om vi har fler linjer behövs return och {}, flera argument kan skrivas i (Arg, Arg)	


```
const percentageOfWorld3 = populationInMi3 => (populationInMi3 / 7900) * 100;
console.log(percentageOfWorld3(1441));
or:
const greet = () => "hello world!";
```


**Rest … (Rest parameter för functions) <code>...<em>numbers</em></code></strong>


```
const add = function (...numbers) {
  let sum = 0;
  for (let i = 0; i < numbers.length; i++) sum += numbers[i];};
add(2, 3)    add(5, 3, 7, 2);       add(8, 2, 5, 3, 2, 1, 4);
```


**Optional chaining (?.) för methods.**


```
.log(restaurant.order?.(0,1) ?? "Method does not exist");
```


Op. chaning ?. kollar om det till vänster existerar (order) och det skrivs ut “Metod does..” om det inte pga ?? nullish assignment operator. Op chain används OFTAST med ??

Alla JS funnktioner är First-class function = functions are values (teori)

**Higher-order function och call-back function**.


```
const oneWord = function (str) { return str.replaceAll(' ', '').toLowerCase();};
const transformer = function (str, fn) { //Higher order function
  console.log(`Original string: ${str}`);
  console.log(`Transformed string ${fn(str)}`); >> Callback
  console.log(`Transformed by ${fn.name}`);};   >>> Name prop på funktionen

transformer('Javascript is the shit', oneWord); //oneWord e Callback funct.

const high5 = function() (console.log("High Five!"));
document.body.addEventListener('click', high5) 
high5 callback function, addEventListener = higher order function
Dom högre order, lämnar detaljerna till underliggande funktioner.
```


**Functions, returning function**


```
const greet = function(greeting) {
return function (name) {return `${greeting} ${name}}`;}}
const greeterHey = greet("Hey");
greeterHey("Andreas")   <<< Om man har en funktion, men många underfunktioner som ändras exempelvis
greet('Hello')('Andreas');
```


Som arrow:


```
const greet2 = greeting => name => console.log(`${greeting} ${name}`);

const calcTAX = function (rate) {
  return function (value) { return value + value * rate }}
const vat10Perc = calcTAX(0.1);
console.log(vat10Perc(100));
```


**Immediately Invoked Function Expressions (IIFE)**

Privata variabler pga scope chain.


```
(function () {code})() ; Sista () är för att kalla den.
```



## Array, Set, Object eller Map?



<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")


Array of objects är troligtvis det vanligaste (JSON > JS object exempelvis)

Array/Set >> Array: ordning, dubletter, ändra data, 

Array/Set >> Sets: Unika värde, performance (sök, ta bort = mkt snabbare), 

Object/Maps: Object: **Enklare **att skriva och få access, används generellt

Object/Maps: Maps: Performance, använd när key behöver vara annat är string, kan ej ha function methods.


## Arrays

What array to use: [https://www.udemy.com/course/the-complete-javascript-course/learn/lecture/22648787#learning-tools](https://www.udemy.com/course/the-complete-javascript-course/learn/lecture/22648787#learning-tools)



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")


<code><em>const</em> arrayName = [5, 87, 32, 234];</code>   &lt;<&lt; Vanligast


```
const arrayName = new Array(1,2,3); <<< samma som ovan

const arrayName = Array.from({ length: 7 }, (element, index) => index + 1);
I array.from anges förs längden och sen en liknande .map function.

const getArrayItem = arrayName[2]; >>> Get array elemnt by ID
const getArrayItem = arrayName.at(2); >>> Get array elemnt by ID
const getArrayItem = arrayName.at(-1); >>> Kan få sista + method chain

let arrayLength = arrayName.length; >> Längden (OBS 0 första)
```


**Array methods (Operations)**


```
// Lägg till/ta bort
arrayLength = arrayName.push(25); >> Add element + retur av längden
arrayLength = arrayName.unshift(66); >> Add element i början, retur av len
let rmElement = arrayName.pop(); > tar bort sista, retur av element
let rmElement = arrayName.shift(); > tar bort första, retur av element

// SÖK
arrayName.indexof("element") >> Ger index på var element ligger (-1 annars)
arrayName.includes("element") >> True/False om elementet finns (Strict!)
```


newarray = oldarray.map(x => x * 2) > skapar ny array med info från den gamla.


```
const newArr = arrName.slice(2); >> Från element 2 och fram, ny array
const newArr = arrName.slice(2, 4); >> Från element 2 till 4
const newArr = arrName.slice(-2); >> 2 sista elementen
let rmElement = arrName.splice(2); >[M]> Tar bort i orginal arrayn, retur
arrName.splice(2, 2); >[M]> Börjar på 2 och fortsätter 2 element bort
arrName.reverse() >[M]> Reverse… ändrar i orginal arrayn
const sumArray = arrName.concat(array2); > lägger ihop/joins
const aString = arrName.join(', ');  >> Array till string, seperator
ArrName.sort(); //Sorterar strings. >M> MUTERAR strängen!
ArrName.sort((a, b) => a - b); //Om man sortera integers ascending!
ArrName.sort((a, b) => b - a); //Om man sortera integers de-scending!
```


Undvik chain om det ändrar orginal array, som ex splice och reverse.

**Array-destructuring:**


```
const arr = [1,2,3];
const [x, y, z] = arr; (behöver inte vara alla tre)
let [x, ,y] (kan också lämna noll i mitten)
[y, x] = [x, y] för att sen ändra ordning.
const [a, b] = funcName(x, y); funktion retur array, kan destr användas.
const  [a, [b,c]] = nestedArray; ([1,[2,3]])
Om man gör destruct på för många värden = undefined. Kan ha default value:
const  [a=1,b=1,c=1] = nestedArray; [5,5] - kommer ge c=1 pga default value
```




<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image3.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image3.png "image_tooltip")


**Spread … (funderar på array, string (varje bokstav), maps and sets.	**

**Kan vara användas när man bygger en array. Separerar med ,**


```
// SPREAD, foldar ut en hel array
const arr = [3, 4, 5]; istället: ([1, 2, arr[0], arr[1], arr[2]])
const newArr = [1, 2, ...arr];
const newMenuArray = [...restaurant.mainMenuArray, 'Gnocci'];
```


**Rest … används på vänster sida om =**


```
const [a, b, ...others] = [1, 2, 3, 4, 5]; 
  = skapar 1,2 och en ny array med 3,4,5 som heter others
```




<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image4.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image4.png "image_tooltip")


**Loop/Loopa genom an array / array loop**


```
for (const item of arrayVar){console.log(item)};
```


För att få id OCH element


```
for (const [i, el] of arrayVar.entries()) {console.log(`${i}: ${el}`);
```


**For Each loop **(Continue och break finns inte i For/Each)


```
arrayVar.forEach(function(element, index, entireArray) { code })
```




<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image5.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image5.png "image_tooltip")


**Map **Loopar igenom alla värden, beräknar och gör en ny array.


```
const newArr = arrayVar.Map  (Ex current * 2)
movements.map(function(value, index, array));
Ex [3,1,4,2,3] blir [6,2,8,6,4]
```


Usecase:


```
const movementsEUR = [200, 450, -400, 3000, -650, -130, 70, 1300];
const conversionRate = 1.1;
const movementsUSD = movementsEUR.map(function(value, index, array){
return value * conversionRate;});
>>> eller >>> 
const movementsUSD = movementsEUR.map(value => value * conversionRate);
```


**Filter **Loopar igenom alla värden, filtrerar och gör en ny array.


```
const newArr = arrayVar.filter  (Ex current > 2)
Ex [3,1,4,2,3] blir [3,4,3]
```


Usecase:


```
const deposits = movements.filter(function (mov) {return mov > 0}); True/F
>>> eller >>>
const deposits = movements.filter(mov => mov > 0);
```


**Reduce **Loopar igenom alla värden, reduserar till ett värde och gör en ny array.


```
const newArr = arrayVar.filter  (Ex acc + current)
Ex [3,1,4,2,3] blir 13
```


Usecase:


```
const balance = movements.reduce(function (accumulator, value, index, array) {return accumulator + value;}, 0); >> Börjar på 0
>>> Eller >>>
const balance = movements.reduce((accumulator, value) => accumulator + value, 0);
const count = arrayName.reduce((count, value) => value => 1000 ? count + 1 : count, 0); >>> Count how many times value is above 1000
```


**Find **Array find array, fungerar som map (loopar och försöker hitta). Return det första elementet som är korrekt.


```
const newArr = movements.find(toFind => toFind < 0);
const newArr2 = accounts.find(toFind => toFind.owner === 'Name');
```


Usecase:


```
const
```


**Flat/Flatmap**


```
const arr = [[1, 2, 3], 4, (5)[(6, 7, 8)]];
const allArr = arr.flat(); //Samlar alla arrays in en (En level)
const allArr = arr.flat(2); //Om man har fler levels (Arr i arr i arr)
```


usecase


```
const overallBalance = accounts
  .map(acc => acc.movements) //Take all movements in account arr
  .flat() //Flat the arrays into one array
  .reduce(acc, mov => acc + mov, 0); //Reduce into a total
```


Map + Flap är väldigt vanligt, därför finns flatmap: MEN BARA 1 LEVEL!


```
  const overallBalance = accounts
  .flatMap(acc => acc.movements) //Take all movements in account arr
  .reduce(acc, mov => acc + mov, 0); //Reduce into a total
```


**FindIndex **Array find array, fungerar som map (loopar och försöker hitta). Return det första elementet som är korrekt med ett index nr.


```
 const index = accounts.findIndex(acc => acc.username === currentAccount.username);
 >>> Usecase: accounts.splice(index, 1);
```


**Some **loopar array och ger true/false om **ETT **condition uppfylls


```
const anyMovOver1000 = movements.some(move => move > 1000);  /True or false
```


**Some **loopar array och ger true/false om **ALLA **condition uppfylls


```
const allMovOver1000 = movements.every(move => move > 1000);  /True/false
```



## Objects


## _const_ openingHours = {


##   [weekdays[3]]: {


##     open: 12,


##     close: 22,


##   },


##   [weekdays[4]]: {


##     open: 11,


##     close: 23,


##   },


##   [weekdays[5]]: {


##     open: 0, // Open 24 hours


##     close: 24,


##   },};

namn.key för att få ut data från ett object, måste skrivas exakt.

namn[key] här kan du beräkna fram vad som ska stå (languageObj[language])

|| default om det inte finns något att hämta: languageObj[language] || "Welcome";

Lägga till object från object, räcker med:


## _const_ person = {


##   firstName: "John", 


##   <span style="text-decoration:underline;">location</span>, {;  &lt;< Om det finns ett object i global/ovan som heter så

**Kopiera object:**

<span style="text-decoration:underline;">Method borrowing</span> - behöver inte skriva ett object 2 ggr, kan göra en = … men:

Object skapas i “heap” och variablen som ligger i call stack länkas till heap. Så om man kopierar ett object skapar man egentligen bara en kopia av variablen som länkar till samma objekt. Det innebär att om man ändrar objektet ändrar man för båda variablerna eftersom det bara finns ett objekt. **Detta gäller också i funktioner! **Om man ändrar ett objekt som passerats in i en funktion, ändrar man i orginalet. Detta gäller ej variabler.


```
const passanger = {Name: 'Andreas', Passport: 98743208437,};
const checkin = function (flightNo, pass) {
  if (pass.Passport === 98743208437) alert('Checkin');
  pass.Passport = -1;	<<< reflekteras ÄVEN i passanger object.
};
checkin(flight, passanger);      <<< first time passp is 98743208437
console.log(passanger.Passport); <<< nu -1 !
```


För  att kopiera ett object i heap måste man: 

const nyttObject = <span style="text-decoration:underline;">Object.assign</span>({}, gammaltObject) 



* {} innebär nytt object, fungerar bara på översta leveln av objekt (shallow copy) och inte om det finns ett objekt i objektet

Bättre att använda …spread operator

const nyttObject = <span style="text-decoration:underline;">{...gammaltObj}; &lt;<&lt; </span>

**Object Methods:**

**En funktion/method inom ett object:**


```
  orderDelivery: function (mainIndex, time) {
console.log('Order received! ${this.mainMenu[mainIndex]} at ${time}`)};
Kan enkelt skrivas i object (ES6): 
  orderDelivery: (mainIndex, time){};
```


**Calling a function with object in object (<code>orderDelivery)</code>:</strong>


```
const restaurant = {
  name: 'Classico Italiano',
  location: 'Via Angelo Tavanti 23, Firenze, Italy',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic'],
  starterMenu: ['Focaccia', 'Bruschetta', 'Garlic Bread'],
  mainMenu: ['Pizza', 'Pasta', 'Risotto'],
  orderDelivery({ starterIndex = 1, mainIndex = 0, time = '20:00', address }) {
console.log('Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`    );}

restaurant.orderDelivery({
  address: 'Via del Sole, 21',
  starterIndex: 1,
});
```


**Object-destructuring**


```
const restaurant = {
  name: 'Classico Italiano',
  categories: ['Italian', 'Pizzeria', 'Vegetarian', 'Organic']

 = destr objectet med nya variabelnamn	
const { name: newVarName, categories: newVarName2 } = restaurant;
 = default value om den inte finns, annars undefined
```



## _const_ { name: newVarName = [] } = restaurant;


```
 = Mutating variables
let a = 111; let b = 999; <<< A, B redan definierade.
const obj = { a: 23, b: 7, c: 14 };
({ a, b } = obj);      <<< behöver sätta detta i parantes.
 = Nested objects (fri är ett object inne i openingHours)
const {fri: { open: oVar, close: cVar }} = openingHours;
```


**Object methods/operations**

kan ha function expression i objects >>> key: function(att) { code }

används som **Function Expression **(eftersom det är ett value)** **inom objektet:


```
const objectAndreas = {
  percentageOfWorld2 : function (populationInMil2) {
    return (populationInMil2 / 7900) * 100; } 
};
```


**Rest … används på vänster sida om =**


```
const { sat, ...weekdays } = restaurant.openingHours;
  = skapar en variabel med sat och en ny array med alla veckodagar
```


**Optional chaining (?.) för Objects.**


```
restaturant.openingHours?.monday?.open
```


Om man inte vet om en property existerar, sätter man ?. efter (openinghours och monday i exemplet). Om den inte finns kommer inte .open läsas. Om man inte gör detta kommer det bli undefined error.


```
for (const day of days) {
  const open = restaurant.openingHours[day]?.open ?? 'closed';
  console.log(`On ${day}, we open at ${open}`);}
```


Exempel på optional chaining: loopa igenom en array, om day inte finns så kollas inte open, ?? ger “closed” pga the assignment nullish operator ??

**Looping Object (Keys, Values, Entities)**


```
const properties = Object.keys(openingHours); >> Array med prop/keys
for (const day of properties) {};  >> Looper genom properties
const values = Object.values(openingHours); >> Array med values
const entries = Object.entries(openingHours); >> Array/ array keys/values
for (const [day, { open, close }] of entries) {} >> Deconstr + loop	
```


K


```


## Object.freeze(
```


Kommer frysa objectet så man inte kan lägga till grejer men det går att ändra


## Sets

Kan aldrig ha dublettet, alltid unika. Usecase: Hitta unika värde i Array


```
const ordersSet = new Set([
  'Pasta', 
  'Pizza',
  'Pizza',   << dubletter tas bort
  'Risotto',
  'Pasta',   << dubletter tas bort
  'Pizza',  << dubletter tas bort
]);

orderSet.size    >>> Storleken (length) 3 i exemplet ovan, unika
orderSet.has('Pasta')   >>> True/False
orderSet.add('Bread');  >>> Lägg till nytt (läggs till om unikt)
orderSet.delete('Bread');  >>> Lägg till nytt (läggs till om unikt)
orderSet.clear()
```


Kan inte använda orderset[0] - finns inget index, eller få ut värde. Behöver bara veta om det finns eller ej.


```
for (const setInfo of orderSet) {console.log(setInfo)};  >> Loopa
```


_const_ staff = ['Waiter', 'Waiter', 'Chef'];  >> Göra Array till unik array

_const_ UniqueStaff = [...new _Set_(staff)];

Loopa Set:


```
orderSet.forEach(function(value, _, Map) { code })
```



## Maps

Maps är object, men key kan vara vilken datatyp som helst


```
mapName.set('Name', 'Andreas');
mapName.set(1, 'Carens');  >> Set lägger till nytt.
mapName.set(2, 'Ceed');  >> Kan vara vilken datatyp man vill som key
console.log(mapName.set(2, 'Ceed'));  >> Set gör alltid en retur
mapName
  .set(3, 'Ferrari')
  .set('Model', 'Spider')
  .set('Fotbollstars', game.scored)
  .set(true, 'For sale')
  .set(false, 'Not for sale')
  .set("Price", 1000000);
```


Enklare sätt att lägga till maps: (array of arrays)


```
const question = new Map([
  ["Question", "Best language?"],
  [1, "C"],
  [2, "Jawa"],
  [3, "JavaScript"],
  ["correct", 3],
  [true, "Correct!"],
  [false, "Try again"]
])
```


Usecase


```
console.log(questionMap.get("Question"));
for (const [key, value] of questionMap) {
if (typeof key === "number") console.log(`Answer: ${key}: ${value}`)}
const answer = Number(prompt("Your answer"));
/console.log(questionMap.get(questionMap.get("correct") === answer));

mapName.has("Model") >>> True/False
mapName.delete('Name');
mapName.size;
mapName.clear();
[...mapName.entries()];
[...mapName.keys()];
[...mapName.values()];
```


Enkelt sätt att göra object till map:


```
const openingHoursMap = new Map(Object.entries(restaurant.openingHours));

const offerPrice = 900000;     >>> Usecase:
const sale = rest.get(mapName.get('Price') <= offerPrice);
>> Är true/false och hämtar då true/false från map.
```


Kan även ha array som key, men måste först definieras som en variabel


```
const arr = [1,2,3]
mapName.set(arr, "hello")   <<< OK
mapName.set([1,2,3], "hello")  <<< FUNKAR EJ

mapName.set(document.querySelector("h1"), "hello"); 
<<< Key kan peka till DOM (avancerat!)
```


Map till array


```
const newArr = [...questionMap];
```


Loopa Map:


```
mapName.forEach(function(value, key, Map) { code })
```



## .This keyword

Special variabel som alltid **kallar **på objectet (“ägaren”) man är i. Inte i objectets namn, utan det som kallar.

	


```
const objectAndreas = {
  Population: 500, 
  percentageOfWorld2 : function () {
    return (this.Population / 7900) * 100; } 
};
```


this.nykey kan användas för att skapa nya properties:


```
const objectAndreas = {
  Population: 500, 
  percentageOfWorld2 : function () {
    this.populationCalc = (this.Population / 7900) * 100;
    return this.populationCalc; } 
};

```



* .this pekar globalt till window som är ägaren. I strict mode pekar den till undefined i övriga funtioner som ej tar upp this, utan strict alltid till window.
* Tar INTE upp någon från en **arrow **function - utan tar upp this från högre upp function, window om det är sista nåbara. _Detta kan vara användbart om man har en arrow funktion inuti någon annan funktion som kallas med this._
* I en eventlistener är det alltid det DOM element som eventlistener är startad med.


## Call / Apply / Bind

**<span style="text-decoration:underline;">.call</span>**


```
function.call(this keyword, arg1, arg2)  >>> manuellt sätta .this keyword
```


usecase: En global funktion som använder this och kan anvöndas i flera objekt


```
const airliner = {
  bookings: [],
  book(flightno, passname) {console.log(flightno);}};
const airliner2 = {bookings: []};
airliner.book('123', 'Andreas'); >> Funkar fint!
const book = airliner.book;
book('123', 'Andreas'); >> Funkar INTE! (.This pekar på global)
book.call(airliner2, '987', 'Emma');   >> Funkar! 
```


**<span style="text-decoration:underline;">.apply</span>**

Fungerar på samma sätt som call, men med en array av data för argumenten, men det används sällan pga spread operator


```
const flightArray = [746, 'Jonas'];
book.apply(airliner, flightArray);
book.call(airliner2, ...flightArray);
```


**<span style="text-decoration:underline;">.bind</span>**

bind används för att sätta olika argument i STEN


```
const bookA2 = book.bind(airliner2); >> Ny funktion med this. bindat.
const bookA2F111 = book.bind(airliner2, "A111"); >> Ny funktion med this. bindat samt flight number. "Partial application"
const bookA2F111 = book.bind(null, "A111"); >> Null om ej this.
```


Viktigt att order av argumenten är rätt!


```
document.queryselector(".buy").addEventlisterner("click", airliner.newFunction.bind(airliner)) <<< bind this to airliner in el.
```



## Loop (For)

for(start; hur länge (true/false; steps) 


```
for (let counter = 1; counter <= 10; rep++) {  }
```


Loop through array:


```
for (let i = 0; i < Arrayname.length; i++) {
    console.log(arrayname[i];)	}
```


Continue (starta om loopen på nästa i) / Break (stäng av loopen helt).

While loop, när man inte har counter utan loopar beroende på en varabel - ex en tärning så länge tärningen inte slår 6.


```
while (dice !== 6) {
    dice = Math.trunc(Math.random() * 6 + 1) }
```



## Timeouts Intervals

Action kommer utföras efter 5000ms, kan kalla funktion eller göra något.

Schmalägga “senare” - koden stoppar INTE.


```
const timeoutV = setTimeout((a1, a2) => console.log(`Action will perform after MS > with argument ${a1} and ${a2}`),5000,'Argument 1','Arg2');
Some condition {clearTimeout(timeoutV)};  << Stannar om kallas inom ms
```


Kör function varje 5000ms (loop)


```
setInterval(function () {
  const now = new Date();
  console.log(now);}, 5000);
```



# Object Oriented Programming (OOP)

I objects, data och behaviours (kod, functioner, methods)


## Classes I Prototype

Class (Blueprint of object) >SKAPAR> Instance (object med data från blueprint)

I JS har varje objekt en länk till en prototype. Prototype innehåller methoder/properties som varje object som länkas till kan access. Object delegerar till prototype objectet.

**Constructor function eller instance**


```
const Person = function (firtName, birthYear) {};
```


constructor functions (blueprint) startar med stor bokstav


```
new Person('Andreas', 1984);
```


new keyword gör:



1. Skapar ett nytt object {}
2. Constructor function kallas, this = {} tomma nya objectet
3. Länkas till prototyp (`Andreas.__proto__ === Person.prototype;)`
4. automatisk retur av {} fr construktor function


```
const Person = function (firtName, birthYear) {
  this.firstname = firtName   << instance property
  this.birthYear = birthYear};
  //Gör ADLRIG detta i constructor, funktionen följer med alla nytt object.
  //   this.calcAge = function () {2022 - birthYear};
const Andreas = new Person('Andreas', 1984);
const Emma = new Person('Emma', 1987);
const Malwa = new Person('Malwa', 2009);
console.log(andreas instanceof Person);   <<< Kommer vara true
```


Kan också (**ES6**) skapas med nya begrett (samma, men enklare - men gömmer den sanna bakomliggande processen - debateras om detta är bra)


```
class PersonCL {
  constructor(firstname, birthyear) {
    this.firstname = firstname;
    this.birthyear = birthyear;
    this._account = [];  >>> _name convection som betyder skyddad! 
    this.locale = navigator.language;}
  calcage() {
    console.log(2022 - this.birthyear);}
  get age() {
    return 2022 - this.birthyear;}
  set fullName(fullName) {
    this.fullName = fullName;}
  static hello() {
    console.log('Saying hello');}
  deposit(value) {
    this.account.push(value);}
    return this; 		>>> Gör methoden "chainable"
  withdraw(value) {
    this.deposit(-value);}
    return this; 		>>> Gör methoden "chainable"
}
const jessica = new PersonCL('Jessica', 1980);
jessica.deposit(400);
jessica.withdraw(150).deposit(40).deposit(466);
PersonCL.hello();
```


Alla Person objekt som skapas kommer få tillgång till prototype funktioner.


```
Person.prototype.calcAge = function () {
  console.log(2022 - this.birthYear);};
Andreas.calcAge();
```


species finns sen på alla objekt som skapas:


```
Person.prototype.species = 'Homo capiens';
console.log(Andreas.species);
```


Alla objekt har en prototype - som scopechain - överst oftast object.prototype som innehåller massa funktioner som ärvs ner. Även för DOM elemen och functions (som är object).


## Set/get (i class)

Get och set binder ett objects egenskap (property) till en funktion så man kan kalla den. Set måste alltid ha 1 parameter


```
  get age() {
    return 2022 - this.birthyear}
  set fullName (fullName) {
    this.fullName = fullName  }
```


Istället för (man kallar en funktion)


```
jessica.calcage();
```


blir det att man kallar en egenskap


```
jessica.calcage;
```



## Static methods

En metod/function som **ej ärvs ner**, utan bara kan köras från objectet (se ovan)

**Constructor function:**


```
Person.hey = function() {
  console.log('Saying hello');}
```


**Class**:


```
  static hello() {
    console.log("Saying hello");}}
Person.hey();
```



## Object.create

För att länka prototype manuellt: (skapar tomt object utan Init funktion)


```
const PersonPrototype = {
  calcAge() {
    console.log(2022 - this.birthYear);},
  init(firstname, birthYear) {
    this.firstname = firstname;
    this.birthYear = birthYear;},};
const Steven = Object.create(PersonPrototype);
Steven.init("Steven", 1976)
```



## Inheritance between “classes” / Link prototypes

Via constructor function:


```
const Child = function (arg1, arg2, arg3) {
  Parent.call(this, arg1, arg2);
  this.arg3 = arg3 //Constructor function};
Child.prototype = Object.create(Parent.prototype);
Child.prototype.methodName = 'your Method';
const ChildName = new Child('arg1', arg2, arg3);
```


Via ES6 classes


```
class StudentCL extends PersonCL {
  constructor(firstname, birthyear, course) {
    super(firstname, birthyear); //First!
    this.course = course;}}
```


Via Object.create


```
const childProto = Object.create(ParentProto);
const childObject = Object.create(ChildProto);
childProto.init = function (first, second, third) {
  ParentProto.init.call(this, first, second)  
  this.third = third;},};
```



## Private / Encapsulation


```
this._account = [];  >>> _name convection som betyder skyddad! 
 _calcage()
```


Underscore före en funciton eller variable innebör att den är “skyddad”. Den är inte skyddad, men det är en indikator på att den aldrig ska kallas direkt! Konvetion.

**Private (Nytt)**


```
class ClassWithPrivateField {
  #privateField;
  constructor() {
    this.#privateField = 42;
  }
  #calcage(){ //Private method (future!)
}}
```



## Local Storage

Sparar info till lokala datorn (obs EJ databas - orkar inte mycket, och bytar du browser finns det inte sparat)


```
localStorage.setItem(key, JSON.stringify(this.#string));

 _getLocalStorage() {
    const data = JSON.parse(localStorage.getItem('workout'));
    if (!data) return;
    this.#workouts = data;
    this.#workouts.forEach(work => {
      this._renderWorkout(work);
    });}  >> Kommer tappa prototype chain!
```



# Public APIs

https://github.com/public-apis/public-apis

**AJAX Call (GAMMALT! - Använd fetch nedan)**


```
const xlmrequest = new XMLHttpRequest();
  xlmrequest.open('Get', `https://restcountries.com/v3.1/name/${country}`);
  xlmrequest.send();
  xlmrequest.addEventListener('load', function (e) {
    const [data] = JSON.parse(this.responseText);
    console.log(data);
```


Nytt sätt att hämta API - görs async (se nedan).


```
const getCountryData = function (country) {
  fetch(`https://restcountries.com/v3.1/name/${country}`)
    .then(response => response.json())
    .then(data => renderCountry(...data));};
```



# Async / Sync coding / Promises

Sync = line by line, alert window blockerar och ingen händer/kan göras. Timers osv.

Async är 



* non-blocking, väntar ej på timer utan den körs i bakgrunden.
* Behöver ha en call-back (men alla call-back är ej async).
* img.src=dog.jpg (exempel på att async kan vara ladda en bild)
* Geolocation API, Ajax calls


## Promise

Man kan skapa promise manuellt eller via vissa functioner (fetch, timouts)



* “Pending” medan async task håller på att göras
* “Settled” - async task är klar, kan vara fulfilled (ok) or rejected (error) 
* Consume promise - använd resultatet

.then sätts på allt som är en promise med en callback funktion som executar bör promise är fulfilled


```
let p = new Promise((resolve, reject) => {
  if (Math.random() >= 0.5) {
    resolve('Promise resolved, this value will be in .then');
  } else {
    reject(new Error('This error will be found in .catch'));}});
p.then((message) => {
  console.log(`This is when resolved: ${message}`)
}).catch((message) => {
  console.log(`This is when rejected: ${message}`);})
```


**Fetch **skapar ett **promise, **kan sen utnyttjas i .then


```
const getCountryData = function (country) {
  fetch(`https://restcountries.com/v3.1/name/${country}`)
    .then(response => response.json())
    .then(data => renderCountry(...data));};
```


**Promise rejection (.catch)**

Fångar upp om det blir en rejection av promise.


```
    .then(data => {
      renderCountry(...data, 'neighbour');})
    .catch(err => {
      console.error(`Error in app: ${err}`);
      renderError(err.message);
    });};
```


Det går att skapa egna “errors” som fångas i catch med **.throw new error**


```
if (!response.ok)
        throw new Error(`Country not found (${response.status})`);
```


**.finally, **oavsett vad som händer kommer denna callback kallas.


```
    .finally(() => {
      countriesContainer.style.opacity = 1;});
```


Exempel på promise inkl allt (gamla sättet att göra det)


```
const getJSON = function (JSONUrl, errorMessage = 'Something wrong') {
  return fetch(JSONUrl).then(response => {  <<< will return promise!
    if (!response.ok) throw new Error(`${errorMessage} (${response})`);
    return response.json();});};

const getCountryData = function (country) {
  getJSON(`https://restcountries.com/v3.1/name/${country}`,_)
    .then(data => {
      renderCountry(...data);
      const [dataNeigthbour] = data;
      if (!dataNeigthbour) throw new Error('Neighbour not found');
      return getJSON(     `https://restcountries.com/v3.1/alpha/${dataNeigthbour.borders?.[0]}`,
        'Country not found');})
    .then(data => {
      renderCountry(...data, 'neighbour');})
    .catch(err => {
      console.error(`Error in app: ${err}`);
      renderError(err.message);})
    .finally(() => {
      countriesContainer.style.opacity = 1;});};

getCountryData('sweden');
```


**Promicifying **= göra om callback based async kod till promise ex:


```
const wait = function (seconds) {
  return new Promise(function (resolve) {
    setTimeout(resolve(), seconds * 1000);});};
wait(1)
  .then(() => {
    console.log('I waited 1 sec');
    return wait(1);})
  .then(() => {
    console.log('I waited 1 sec');
    return wait(1);});
```


**Chain Promise**

För att kunna fortsätta måste man alltid “return a new promise”. När man gör så kan man sen fortsätta med .then eller vad man nu vill. I fallet nedan, är det fetch (promise), .json (promise) och sedan i sista .then gör vi manuellt retur av ny fetch (promise) så kan vi fortsätta med .then.


```
const getCountryData = function (country) {
  fetch(`https://restcountries.com/v3.1/name/${country}`)
    .then(response => response.json())
    .then(data => {
      renderCountry(...data);
      const [dataNeigthbour] = data;
h      return fetch(        `https://restcountries.com/v3.1/alpha/${dataNeigthbour.borders?.[0]}`
      );})
    .then(response => response.json())
    .then(data => {
      renderCountry(...data);
```



## Async och await

Syntetisk socker för promises men göra returen/process av ett promise mer läsbart.Ersätter .then .catch

await används på promise, om man inte gör detta kommer det inte bli async och variablen kommer inte vara resultatet av promise utan bara promise “status”.


```
const whereAmI = async function () {
  try {
    const pos = await getPosition();  <<< Promise
    const { latitude: lat, longitude: lng } = pos.coords;
    const revPOS = await fetch(`https://geocode.xyz/${lat},${lng}?geoit=json`); <<< Promise
    if (!revPOS.ok) throw new Error('Unable to fetch geocode');
    const revPOSData = await revPOS.json();  <<< Promise
    const res = await fetch( <<< Promise
      `https://restcountries.com/v3.1/name/${revPOSData.country}`);
    if (!res.ok) throw new Error('Unable to fetch country');
    const [data] = await res.json(); <<< Promise
    renderCountry(data); 
    return `You are in ${revPOSData.city}`; (If returning something)
  } catch (err) {
    console.log(`We have an error in app ${err}`);
    throw err;}}; (If returning error)
```


Om man vill köra promises parallellt, ex ladda ner tre AJAX calls samtidigt.


```
const data = await Promise.all([Promise1, Promise2, Promise2])
Promise.race(Promise1, Promise2, Promise2) > Den som "vinner" blir retur!
Man kan ex göra en timout function som man kör ajax calls .race mot. Med detta kommer timout att bli rejected och vinna, ie du har skapat en funktion som gör att om ett ajax calls tar för långt tid så slutar det.
Promise.allSettled;  > Ingen går i error som .all
Promise.any; > Som RACE fast rejected är ignorerade.
```


Return value from Async function


```
(async function () {
  try {
    const city = await whereAmI();
    console.log(city);
  } catch (err) {
    console.log(err);}})();
```


Await kan sen ES2022 användas i toplevel modul (dvs ej i en async function).

Blockerar dock hela execution av denna mobulen!! Om en modul importerar en modul med top level await kommer den importen att “blockeras” och ta den tid som behövs för await.

Men är bra att använda för att invänta resultatet på en async function (annars får man bara ett promise).


```
const getPokemonStat = async function (idOrName) {
  try {
    const respons = await fetch(
      `https://pokeapi.co/api/v2/pokemon/${idOrName}`);
    const stats = await respons.json();
    return stats;
    //Catch
  } catch (err) {
    console.log(`Error in getPokemonStat:: ${err}`);}};

const PokeMonstat = await getPokemonMove("name");
```



## Try / Catch

Gammalt i JS - om något blir fel, sätt allt du vill testa i block, och om det blir error så tas det upp i catch


```
try { const x = 1;
  x = 2;
} catch (err) {
  alert(err.message);}
```



# Modules



* One module per file
* Varabler är scoped till modulen, måste exporteras/importeras
* Import/export (bara top level, ej inom något block)
* Import/exports är hoisted (måste vara överst)
* i html &lt;script type=”module”>


```
    <script type="module" defer src="script.js"></script>

```



* Laddas asyncronus


```
import './module.js';
```


**Exports**

Named: Sätt export framför method eller variabel du vill exportera.


```
const varWithName = 'Hello';
export const thisFunction = function () {
  console.log(varWithName);};
```


eller


```
export { varWithName as newName, thisFunction };
```


 

**Default: (Bara en sak)**


```
export default function () {
  console.log(varWithName);}
```


**Import**

Named:


```
import { newName as newnewName, thisFunction } from './module.js';
thisFunction();
```


All:


```
import * as ModuleImportName from './module.js';
ModuleImportName.thisFunction();
```


Default:


```
import nameForFunc from './module.js';
nameForFunc();
```



# Dom and Events (7)

Dom = universal connector mellan Javascript och Html (ändra, manipulera)

Html Paragraf/class - kan hämtas från Javascript och CSS

Försök spara data i variabel och inte i DOM. Läs inte från DOM och uppdatera, spara om möjligt.



<p id="gdcalert6" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image6.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert7">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image6.png "image_tooltip")


**//Select DOM element**


```
const header = document.querySelector('.header'); //Select section
('.class')
console.log(document.querySelector('.message').textContent);
document.querySelector('.guess').value << Om det är ett input type="number"

('#id')
const allSections = document.querySelectorAll('.sections'); //Gets nodelist (Not updated)
const section = document.getElementById('section--1'); //Select by ID
const allButtons = document.getElementsByTagName('button'); // Live/HTML collection (Updated live)
```


**Create DOM element**


```
const message = document.createElement('div'); //Create the element with type.
message.classList.add('cookie-message'); // classlist to Element
message.textContent('One way to add text');
message.innerHTML('<br>How to create the html</br>');
```


**Clone element**


```
message.cloneNode(true); //(Klona, true = childelements också?)
h;
```


**Insert DOM element**


```
header.prepend(message); //Add element as first of header
header.append(message); //Add element last in header
header.before(message); //Add element before the header
header.after(message); //Add element after the header

const containerMovements = document.querySelector('.movements');
containerMovements.innerHTML = '';  >> Tömmer hela elementet
containerMovements.insertAdjacentHTML('afterbegin', html); > Insert html
```


**Delete DOM element**


```
message.remove();
```


Dom Element kan bara existera i en kopia! Om man försöker sätta in samma element på olika platser kommer den bara flyttas till sista insättningen.

**Hitta närmsta child eller parent**


```
const h1 = document.querySelector('h1');
//Find Child
h1.querySelector('.highlight');
h1.parentElement():
//Find parent
h1.closest('.header');
h1.children();
//Sibblings (sideways)
h1.previousElementSibling;
h1.nextElementSibling;
```


**Usecase - gå upp ett för att sen välja alla children och göra något. **


```
[...h1.parentElement.children].forEach(el) {
  if (el !==h1) el.style.backgroundcolor = "white"}
```



## Events

Eventlistener - lyssnar på “click”, “keydown” osv…


```
document.addEventListener('keydown', function (e) {
  if (e.key === 'Escape' && !modal.classList.contains('hidden')) {
    closeModal();}});
```


Ovan exempel visar keydown Escape


```
overlay.addEventListener('click', closeModal);
```


Om man vill lyssna på ett keypress event, är detta GLOBALT.


```
document.addEventListener('keydown', function () {
  console.log('A key was pressen / anyone');});
```


i addEventlistener skapas ett object som berättar vad som händer:


```
//keyboard event = global event.
document.addEventListener('keydown', function (event) {
  console.log(event.key);});
```


Lägg till bara console.log för att läsa hela eventet som är stort och innehåller massa info.

**Remove Eventlistener**


```
const h1 = document.querySelector('h1');
const alertHE = function () {
  alert('AddEvent');
  h1.removeEventListener('mouseenter', alertHE);
};
h1.addEventListener('mouseenter', alertHE);
```


**Lägger EventListener på “parent” och tar alla events (som QuerySelectoAll + ForEach), Viktigt ex om  man har många child eller elementet inte finns från början utan adderas med kod.**


```
//1. Add EventListener to common parent
document.querySelector('.nav__links').addEventListener('click', function (e) {
  e.preventDefault();
  //2 Find element that determined the event
  if (e.target.classList.contains('nav__link')) {
    const id = e.target.getAttribute('href');
//Do Something:
    document.querySelector(id).scrollIntoView({ behavior: 'smooth' });}});
```


**Guard clause**


```
  const clicked = e.target.closest('.operations__tab');
if (!clicked) return; //Guard clause (If null) << Clean instead of IF () {
  clicked.classList.add('operations__tab--active');});
```


**IntercectionObserver (triggar när section korsar viewport eller section:**


```
const observerOptions = {
  root: null, //null = viewport, men kan vara annan intersection
  threshold: [0, 0.2]}; //0 = in/out helt av view. 1=100% MÅSTE vara synlig
//new IntersectionObserver(callback, options)
const observer = new IntersectionObserver(function (entries, observer) {
  entries.forEach(ent => console.log(ent));}, observerOptions);
observer.observe(section1);//isInterceting = true när man scrollar förbi
```


**UseCase (Sticky header)**


```
const stickHeader = function (ent) {
  const [entry] = ent;
  if (!entry.isIntersecting) nav.classList.add('sticky');
  else nav.classList.remove('sticky');
};
const headObserver = new IntersectionObserver(stickHeader, {
  root: null, threshold: [0, 0.2], rootMargin: `-${nav.getBoundingClientRect().height}px`});
headObserver.observe(document.querySelector('.header'););
```


**Usecase (ta fram gömda sektioer)**


```
const allSections = document.querySelectorAll('.section');
const revealSection = function (entries, observer) {
  const [entry] = entries;
  if (!entry.isIntersecting) return;
  entry.target.classList.remove('section--hidden');
  sectionObserver.unobserve(entry.target);};
const sectionObserver = new IntersectionObserver(revealSection, {
  root: null,
  threshold: 0.15,});
allSections.forEach(section => {
  section.classList.add('section--hidden');
  sectionObserver.observe(section);});
```



## Html attributes


```
<img                < Element
src="img/logo.png"  < Attribute
alt="Bankist logo"
class="nav__logo"
id="logo"/>
```


Read and Write attributes


```
const logo = document.querySelector('.nav__logo');
const scr = logo.scr; //READ
const scr = logo.getAttribute('non-standard attr'); //READ NON STANDARD
logo.alt = "Hello alternative text" //Write
logo.setAttribute('NonStandAttr', "AttrKey"); // Write Non standard attr.
```


Data-Attributes (speciella som alltid börjar med data-


```
        <img src="img/logo.png"
          data-version-number="3.0"/>
const version = logo.dataset.versionNumber;

<article
  id="electric-cars"
  data-columns="3"
  data-index-number="12314"
  data-parent="cars">
</article>

const article = document.querySelector('#electric-cars');
// const article = document.getElementById("electric-cars")
article.dataset.columns; // "3"
article.dataset.indexNumber; // "12314"
article.dataset.parent; // "cars"
```


Select all img with data-src as data attribute


```
const imgTarget = document.querySelectorAll('img[data-src]');
```



## Ladda in din JS eller andra scr file

Ofta i slutet på &lt;body> för att HTML/DOM ska laddas innan script fire


```
    <script src="script.js"></script>
  </body>
```


Ska HELST använda defer, där script hämtas under pågående DOM/HTML med exec efter.


```
<head>  
  <script defer src="script.js"></script>
```


Även async som är snabbast, men ej för egna libraries eller resurser som man behöver.


## Style/Css ändringar

For CSS manipulering - använd .style.css property (camelcase notation). Value måste alltid vara String! `document.querySelector('body').style.backgroundColor = '#60b347';`


```
document.querySelector('.number').style.width = '30rem';
message.style.backgroundColor = 'Grey';
message.style.width = '120%';
```


Går dock INTE att läsa en style som inte satts via kod, dvs ej från CSS filen utan får då:


```
getComputedStyle(message).color;
```


**Classes**

Ofta lägger man till och tar bort hela CSS klasser, som då påverkar utseendet på hemsidan. Ex .hidden


```
const closeModal = function () {
  modal.classList.add('hidden');
  overlay.classList.add('hidden');
};
btnCloseModal.addEventListener('click', closeModal);
overlay.addEventListener('click', closeModal);

 modal.classList.add('classname', 'secondname');
 modal.classList.remove('classname');
 modal.classList.toggle('classname');
 modal.classList.contains('classname');
```


**CSS Variabler**

I CSS kan man definiera css variabler som sen kan ändras via JS


```
:root {
  --color-primary: #5ec576;
  --color-secondary: #ffcb03;
>>> CSS Fil ovan, JS nedan <<<
document.documentElement.style.setProperty("--color-primary", "Grey")
```



## Dom Functions


```
inputLoginPin.blur(); //Loose focus
btnTransfer.addEventListener('click', function (event) {
  event.preventDefault();  //I forms, gör så den inte reloadar
```



## Koordinater, Storlek Window


```
console.log('Current position/Scroll (X/Y)', window.scrollX, scrollY);
 << se nuvarande position (top/left) i pixels
console.log('Current width/height (X/Y)', document.documentElement.clientHeight,document.documentElement.clientWidth
  ); <<< Storleken på viewport
```


**Scrolla till view**


```
const BtnStartScroll = document.querySelector('.btn--scroll-to');
const sectionToScrollTo = document.querySelector('#section--1');
BtnStartScroll.addEventListener('click', function () {
  sectionToScrollTo.scrollIntoView({behavior: 'smooth',});});
```



# Bundle, Transpile Polyfill and deploy

**Bundle: Parcel**

(Install) sudo npm i parcel

npm scripts för att köra i package.json: 


```
"scripts" : {
  "start": parcel index.html
  "build": parcel build index.html
}
```


npm run start i commandline

ta bort type:”module” i html

skapar dist folder och kör en live-server

hot module replacement:


```
if (module.hot) {
  module.hot.accept()}
```


Will inject new data/changes without reloading.

npm run build för final build (compressed).

Nu hittar man inte länkarna längre. Kan importera hela kataloger istället:Gäller video, bilder, ikoner, media.


```
import icons from 'url:../img/icons.svg';
```


**Transpile: Bable**

Gör om syntax till “gammal” kod - så alla kan köra websidan.

(Plugin: single feature  -  preset = tllbaka till en speciel version).

**and Polyfill: **

Gör om promise, find etc till “gammal kod”

npm install core-js


```
import "core-js/stable"
```


Gör inte om koden, itan skapar referenser till gammal kod.

Polyfill async functions:

npm install regenerator-runtime


```
import "regenerator-runtime/runtime"
```



# Architecture

MVC Model

WEB | MODEL &lt;> CONTROLLER &lt;> VIEW | USER

**Model**: Business logic, State (data), HTTP Library

**Controller**: Application login

**View**: Presentation logic



<p id="gdcalert7" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image7.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert8">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image7.png "image_tooltip")


config.js = alla “globala” constants, dvs om du ex har en API URL eller annat. Skrivts oftats med stora bokst

helpers.js = common functions för hela appen.

**Publiseher/Subscriber.**

När man har moduler som inte känner till varandra kan man ha en publisher som triggsas vid något event och en subscriber som sen vill executa.

Controller (känner till view)


```
  recieptView.addHandlerRender(controlReciept);
```


View (känner ej till controller)


```
  addHandlerRender(handler) {
    window.addEventListener('hashchange', handler);
    window.addEventListener('load', handler);  }
