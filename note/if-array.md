if( typeof someVar === 'object' ) {
    // Object
}
   
if( Object.prototype.toString.call( someVar ) === '[object Array]' ) {
   // Array
}

if (Array.isArray(someVar)) {
    // Array
}