# Clutter

## Feel free to test it out yourself here: https://wizardly-goldberg-2c2922.netlify.app 

### Clutter is an app designed to help with your... you guessed it... Clutter!
#### You are able to create an account and store folders of images on it for free!
#### It is secure and your account is your own, no need to share space, leave your clutter here and come get it as you need it.

Build with React and Firebase

Using Firebase for storage and authentication
Using React for Routing and styling
Using React Bootstrap for easy sleek styling
Using Font Awesome for Icons

Created a custom hook to deal with folder structure in the app

Used the React useLocation state to keep data loaded for quick page navigation eve nwith slow internet speeds

Used React Portals (Struggled) for the progress bar for uploading images

#### FireBase Rules:
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      function authed(){
      	return request.auth != null
      }
      function matchesUser(data){
      	return request.auth.uid == data.userId
      }
      function notUpdating(field){
      return !(field in request.resource.data || resource.data[field] == request.resource.data[field])
      }
      allow read: if authed() && matchesUser(resource.data)
      allow create: if authed() && matchesUser(request.resource.data)
      allow update: if authed() && matchesUser(resource.data) && notUpdating("userId")
    }
  }
}


#### Imports/Installs
npm i uuid
npm install --save @fortawesome/react-fontawesome    
npm install --save @fortawesome/free-solid-svg-icons    
npm i --save @fortawesome/fontawesome-svg-core     
npm i react-router-dom  
npm i bootstrap react-bootstrap      
npm i firebase    
