# Lista de errores

"outDir"

para arreglar este error, se tiene que corregir una linea

"rootDir": "./src",
"outDir": "./dist/out-tsc",

Este error aparece cuando la carpeta src no es reconocida de manera adecuada 

# Como cambiar el port en angular

en la raiz del proeycto se encuentra un archivo angular.json

tienes que ir por esta jerarquía del json 

${->projects->architect->serve->options->port

