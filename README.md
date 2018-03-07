# univalid-strategy-default

Default strategy for [univalid](https://github.com/StetsD/univalid) module.

Extends [univalid-strategy](https://github.com/StetsD/univalid-strategy) class


## Install

```sh
npm i univalid-strategy-default
```


## Usage

```js
const UnivalidStrategyDefault = require('univalid-strategy-default');
const usd = new UnivalidStrategyDefault();
```


## API


### applyFilter(filter, val)

Tests the pattern matching of symbols (by event)

**filter** - Type `string`

In current moment available patterns:
* oL - only latin symbols
* oC - only cyrillic symbols
* oN - only numbers
* oP - only numbers and latin symbols

**val** - Type `string`


### check(pack, core)

Validating the pack

**pack** - Type `object`

Structure of pack must be strict. Like that:

name, val, type - required fields
```js
//name, val, type - required fields

[
    {
        name: 'username',
        val: 'Uriy',
        type: 'required',
        filter: 'oL',
        msg: {
            empty: 'You shall not pass',
            invalid: 'Validation error',
            filter: 'Filter error',
            success: 'All right'
        }
    },
    {
        name: 'email',
        val: 'Uriy@mzf.com',
        type: 'email',
        filter: /[a-z]|\s/gi,
        msg: {
            empty: 'You shall not pass',
            invalid: 'Bad email',
            filter: 'Only lat/numbers/specials symbols',
            success: 'All right'
        }
    },
]
```

**core** - Type `object`

The instance of 'univalid' module



### getValidationHandlers()

Get validation handlers.

By default defined in [univalid-strategy](https://github.com/StetsD/univalid-strategy) abstract class


### set(option, val)

Set the option in instance

**option** - Type `string`

```js
usd.set('passConfig', {min: 10, analysis: ['hasLowercase', 'hasDigits', 'hasSpecials']});
```


## OPTIONS


### passConfig

Password config

**By default**

{min: 6, analysis: ['hasUppercase', 'hasLowercase', 'hasDigits', 'hasSpecials']}

```js
const usd = new UnivalidStrategyDefault({
    passConfig: {min: 10, analysis: ['hasLowercase', 'hasDigits', 'hasSpecials']}
});
```

## License
ISC©
