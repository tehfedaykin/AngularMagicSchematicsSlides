## Add to Workspace (package.json) 

```json
//package.json
{
  "name": "angular-magic-schematics",
  "version": "0.0.0",
  "scripts": {
    "ng": "ng",
    "start": "ng serve",
    "build": "ng build",
    "watch": "ng build --watch --configuration development",
    "test": "ng test"
  },
  "private": true,
  "schematics": "./fix-it/src/collection.json",
  "dependencies": {
```

Ensure your schematics can be found when you go to run them.