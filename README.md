## firebase-nodejs

# Firebase SDK for Node.js

Get install !!
```
npm install --save firebase-nodejs
```

# Optionals

* selectData 
For select data from firebase
* insertData
For insert data into firebase
* deleteData
For delete data on firebase
* updateData
For update data on firebase
* authUser
For manage user on firebase
* authFacebook
For auth from facebook

# How to use it ?

Create firebase.js on you app folder, and write code below.
You can use data from you firebase project.
```js
import * as firebaseDom from 'firebase-nodejs';

var config = {
    apiKey: '',
    authDomain: '',
    databaseURL: '',
    storageBucket: '',
};
const firebase = firebaseDom.default.firebaseConfig(config);
export default firebase;
```

So you add my code on you another file for use firebase.

# Examples
```js
import firebase from './firebase.js'; //add you firebase.js path
import * as firebaseDom from 'firebase-nodejs';

export class TestApp extends Component{
  constructor(props) {
    super(props);
    this.state = {
      member: {},
    };
  }
  
  getMemberData(){
    let memberData = firebaseDom.default.selectData(firebase, '/member/id/1', 'value');
    // if data is true function return your data, or no data function return false
    if(memberData !== false){
      this.setState({
         member: memberData,
      });
    } else {
      Alert('Not member !');
    }
  }
  
  render(){
     return(
       .
       .
       .
     )
   }
}

```

# Use another

# authUser an authFacebook
You can authen user from firebase, User facebook user loggin only.

Get current user.

```js
const data = firebaseDom.default.authUser.currentUser(firebase);
```

Logon by use facebook access token.
```js
const data = firebaseDom.default.authFacebook(firebase, accessToken);
```

User data.
```js
let currentUserData = firebaseDom.default.authUser.currentUser(firebase);
currentUserData.name = 'new my name';
const status = firebaseDom.default.authUser.updateUser(firebase, currentUserData);
```

User email.
```js
const status = firebaseDom.default.authUser.updateEmail(firebase, 'new_email@mail.com');
```


User delete.
```js
const status = firebaseDom.default.authUser.deleteUser(firebase);
```
Logout !
```js
const status = firebaseDom.default.authUser.logout(firebase);
```

# selectData

```js
const data = firebaseDom.default.selectData(firebase, '/member/id/1', 'value')

```

# insertData

```js
const member = {
  name: 'test',
  age: 17,
}
const insertStatus = firebaseDom.default.insertData(firebase, '/member/id/2', member);

```


# updateData

```js
const member = {
  name: 'test',
  age: 18,
}
const updateStatus = firebaseDom.default.updateData(firebase, '/member/id/2', member);

```

# deleteData

```js
const deleteStatus = deleteData(firebase, '/member/id/2');

```
