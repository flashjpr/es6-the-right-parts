// DISADVANTAGES of arrow functions
//      all arrow functions are anonymous
//      being anon. functions they show as anon. in stack traces
//      BUT:* name inference
//          var foo = x => 3;
//          console.log(foo.name)    will result in "foo"
//
//          when arrow functions are used as a parameter (99.9% of the time), they won't get
//          name inference, so good luck debugging

// ADVANTAGE (reason for it being included in the language)
//  is that arrow functions don't have a this, so they get a lexical this from the 'parent' object
//  ; in other words, arrow functions pass `this` 'down' to their content
var obj = {
    id: 42,
    foo: function foo () {
        // FIX: var self = this;
        setTimeout(function () {
            console.log(this.id)  // PROBLEM: this does not refer to the obj, but to the global

        },1000)
        // FIX:
        // }.bind(this),1000)
    }
};
