# SINUS Webshop - REST API

## Getting Started

1. `cd backend`
2. Install dependencies `npm install`
3. Start the server `npm run start`


### Datamodeller

#### Product

##### Request Body
```javascript
 {
  "title": 'Gretas Fury',
  "price": 999,
  "shortDesc": 'Unisex',
  "longDesc": 'Skate ipsum dolor sit amet...',
  "imgFile": 'skateboard-greta.png'
} 
```

##### Document Model
```javascript
 {
  _id: '39y7gbbZk1u4ABnv', // generated serverside
  title: 'Gretas Fury',
  price: 999,
  shortDesc: 'Unisex',
  longDesc: 'Skate ipsum dolor sit amet...',
  imgFile: 'skateboard-greta.png' // Asset logic on clientside
} 
```

#### Order
##### Request Body
```js
{
  "items": ["productId1", "productId1", "productId2"]
}
```

##### Document Model
```javascript
 {
  _id: 123,
  timeStamp: Date.now(), 
  status: 'inProcess',
  items: [ 
    {
      title: "Tricky",
      price: 799,
      imgFile: "skateboard-generic.png",
      _id: "9E6KXMIdRglW0wbL",
      amount: 2
    }, 
    {
      <etc>
    }, 
    ... 
  ],
  orderValue: 999
} 
```

#### User

##### Request Body
```js
{
  "email": 'greta.thunberg@example.se',
  "password": 'grillkorv123',
  "name": 'Johan Kivi',

  "address": {
    "street": 'Tokitokvägen 3',
    "zip": '123 45',
    "city": 'Tokberga'
  }
} 
```

##### Document Model

```javascript
{
  _id: '6b521d3f-3d15...' // generated server side
  email: 'johan.kivi@zocom.se',
  password: '$$$hashed password$$$', // hashed serverside
  name: 'Johan Kivi',
  role: 'admin', // or customer
  address: {
    street: 'Tokitokvägen 3',
      zip: '123 45',
      city: 'Tokberga'
  },
  orderHistory: [ <orderId1>, <orderId2>, ... ]
} 
```


