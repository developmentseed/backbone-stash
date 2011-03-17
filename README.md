Backbone Stash
--------------
Server-side overrides for Backbone to use `stash` for Model persistence.

### Compatibility

    documentcloud backbone 0.3.3
    developmentseed stash 0.0.1

### Usage

Pass a filepath to the stash directory (will be created if it doesn't exist
yet) when calling `require()`.

    var Backbone = require('backbone');
    Backbone.sync = require('backbone-stash')('data');

    // Backbone.sync will now load and save models from data/

### Conventions

`backbone-stash` stores models in stash using the `model.url` as its key.
Collections retrieve models by matching the Collection url against
the initial portion of the Model url.

    var orange = new FruitModel({id: 'orange'});
    var apple = new FruitModel({id: 'apple'});
    var banana = new FruitModel({id: 'banana'});

    console.log(orange.url()); // fruits/orange
    console.log(apple.url());  // fruits/apple
    console.log(banana.url()); // fruits/banana

    var fruits = new FruitCollection();

    console.log(fruits.url);   // fruits

    fruits.fetch();            // retrieves orange, apple, banana

### Authors

- [Young Hahn](http://github.com/yhahn)

