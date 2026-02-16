A yaml file used to represent data. If you take the data in its simplest form such as key value pairs - YAML, JSON, XML are all used to represent data, it could be data about an organization and all of its employees and their personal details.

## `XML`

```bash
<Servers>
  <Server>
    <name>Server1</name>
    <owner>John</owner>
    <created>12232012</created>
    <status>active</status>
  </Server>
</Servers>
```

## `JSON`

```bash
{
  Servers: [
    {
      name: Server1,
      owner: John,
      created: 12232012,
      status: active,
    }
  ]
}
```

## `YAML`

```bash
Servers:
  - name: Server1
    owner: John
    created: 12232012
    status: active
```

## `Array/list`

Let's say we would like to store the name of 6 cars, the names are formed by the color and the model of the car. To store this, we would use a list or an array, as it is multiple items of the same type of object. In the array, each item is entered with a dash in the front, the dash indicates that it's an element of an array.

## `Dictionary`

A dictionary is a set of properties grouped together under an item. To store different information or properties of a single object, we use dictionary. Dictionary is an unordered collection, whereas lists are an ordered collection. The properties can be defined in any order but the two dictionaries will still be the same, as long as the values of each property match. This is not the same for lists or arrays.

### ``Key Value Pair`

```bash
Fruit: Apple
Vegetable: Carrot
Liquid: Water
Meat: Chicken
```

### `Array/Lists`

```bash
Fruits:
- Orange
- Apple
- Banana

Vegetables:
- Carrot
- Cauliflower
- Tomato
```

### `Dictionary/Map`

```bash
Banana:
  Calories: 105
  Fat: 0.4 g
  Carbs: 27 g

Grapes:
  Calories: 62
  Fat: 0.3 g
  Carbs: 16 g
```
## `When to use a dictionary or a list` -

Example: Let us take a car, a car is a single object and it has properties such as color, model, transmission and price, to store different information or properties of a single object we use a dictionary.

```bash

                 DICTIONARY vs LIST vs LIST OF DICTIONARIES


                          [ Car ]
                            |
        .................................................
        .           .             .                  .
    [Color]      [Model]      [Transmission]       [Price]
      Blue       Corvette         Manual          $20,000


Dictionary:

Color: Blue
Model: Corvette
Transmission: Manual
Price: $20,000

```

## `Dictionary in Dictionary`

```bash

          DICTIONARY  vs  LIST  vs  LIST OF DICTIONARIES


                         [ Car ]
                           |
        ........................................................
        .               .                 .                   .
     [Color]         [Price]         [Transmission]        [Model]
      Blue           $20,000            Manual                |
                                                             .........
                                                             .       .
                                                          [Name]   [Year]
                                                         Corvette   1995


Dictionary in Dictionary:

Color: Blue
Model:
  Name: Corvette
  Year: 1995
Transmission: Manual
Price: $20,000

```

If we want to store the names of six cars, we use a list (or an array) because it contains multiple items of the same type. Since we are only storing the names, we simply use a single list of strings.

```bash
        DICTIONARY  vs  LIST  vs  LIST OF DICTIONARIES


                         [ Cars ]
                            |
        ....................................................
        .         .           .           .          .       .
   [Blue]     [Grey]      [Red]      [Green]    [Blue]   [Black]
  Corvette   Corvette    Corvette    Corvette   Corvette  Corvette



List Of Strings:

- Blue Corvette
- Grey Corvette
- Red Corvette
- Green Corvette
- Blue Corvette
- Black Corvette
```

If we want to store all the information about each car—such as color, model, transmission, and price—we modify the array from a list of strings to a list of dictionaries.

```bash

        DICTIONARY  vs  LIST  vs  LIST OF DICTIONARIES


                           [ Cars ]
                              |
        ................................................................
        .              .              .              .              .   .
     [Car 1]        [Car 2]        [Car 3]        [Car 4]        [Car 5] [Car 6]
        |              |              |              |              |        |
     ......         ......         ......         ......         ......   ......
     .    .         .    .         .    .         .    .         .    .   .    .
   Color  Model   Color  Model   Color  Model   Color  Model   Color  Model Color Model
    |       |       |       |       |       |       |       |       |       |     |
   Blue  Corvette  Grey  Corvette  Red  Corvette  Green Corvette  Blue Corvette Black Corvette
            |               |              |              |              |            |
          Year            Year           Year           Year           Year         Year
          1995            1995           1995           1995           1995         1995
            |
       Transmission
        (Manual/Auto)
            |
          Price
        ($20,000 / $22,000 / $23,000)



List Of Dictionaries:

- Color: Blue
  Model:
    Name: Corvette
    Model: 1995
  Transmission: Manual
  Price: $20,000

- Color: Grey
  Model:
    Name: Corvette
    Model: 1995
  Transmission: Manual
  Price: $22,000

- Color: Red
  Model:
    Name: Corvette
    Model: 1995
  Transmission: Automatic
  Price: $20,000

- Color: Green
  Model:
    Name: Corvette
    Model: 1995
  Transmission: Manual
  Price: $23,000

- Color: Blue
  Model:
    Name: Corvette
    Model: 1995
  Transmission: Manual
  Price: $20,000

- Color: Black
  Model:
    Name: Corvette
    Model: 1995
  Transmission: Manual
  Price: $20,000
```

```bash

Dictionary/Map

Dictionary - Unordered
List       - Ordered

Banana:                     Banana:
  Calories: 105               Calories: 105
  Fat: 0.4 g       =          Fat: 0.4 g
  Carbs: 27 g                 Carbs: 27 g

Array/List

Fruits:                     Fruits:
- Orange                      - Orange
- Apple            !=         - Banana     
- Banana                      - Apple
