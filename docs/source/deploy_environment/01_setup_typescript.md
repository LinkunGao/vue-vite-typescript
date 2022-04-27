# Setup TypeScript

1. The TypeScript cannot check the snytax in Vue `<template> </template>`

   We can use `command+shift+p` in VsCode

   Then search `Settings JSON`, and add this code inside:

   ```json
   {
     "vetur.experimental.templateInterpolationService": true
   }
   ```
