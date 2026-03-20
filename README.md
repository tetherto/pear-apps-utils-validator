# pear-apps-utils-validator

A lightweight and flexible JavaScript library for validating. It provides a simple API to define validation rules for various data types, including strings, numbers, arrays, and objects.

## Table of Contents

- [Table of Contents](#table-of-contents)
- [Features](#features)
- [Security Notice](#security-notice)
- [Installation](#installation)
- [Usage Examples](#usage-examples)
- [Dependencies](#dependencies)
- [Related Projects](#related-projects)

## Features

- Validate strings, numbers, arrays, and objects.
- Built-in validation rules like `required`, `minLength`, `maxLength`, `min`, `max`, `email`, and more.
- Custom validation with `refine`.
- Schema-based validation for objects and arrays.
- Lightweight and easy to use.

## Security Notice

1. To ensure the security and integrity of your projects, please note that official PearPass packages are distributed exclusively through our GitHub organization.
2. Any packages with similar names found on the npm registry or other third-party package managers are not affiliated with PearPass and should be strictly avoided. We recommend installing directly from this repository to ensure you are using the verified, open-source version.

## Installation

Install the library using npm:
```bash
npm install git+https://github.com/tetherto/pear-apps-utils-validator.git
```

## Usage Examples

### String Validation
```js
import { Validator } from '@tetherto/pear-apps-utils-validator';

const validator = Validator.string().required().minLength(3);
console.log(validator.validate('')); // Output: "This field is required"
console.log(validator.validate('ab')); // Output: "Minimum length is 3"
console.log(validator.validate('abc')); // Output: null
```

### Object Validation
```js
const schema = {
    name: Validator.string().required(),
    age: Validator.number().min(18),
};

const validator = Validator.object(schema);
console.log(validator.validate({ name: '', age: 16 })); 
// Output: { name: "This field is required", age: "Minimum value is 18" }
```

### Array Validation
```js
const itemValidator = Validator.string().minLength(3);
const arrayValidator = Validator.array().items(itemValidator);

console.log(arrayValidator.validate(['valid', 'a'])); 
// Output: [{ index: 1, error: "Minimum length is 3" }]
```

## Dependencies

This package has no production dependencies.

## Related Projects

- [@tetherto/pearpass-app-mobile](https://github.com/tetherto/pearpass-app-mobile) - A mobile app for PearPass, a password manager
- [@tetherto/pearpass-app-desktop](https://github.com/tetherto/pearpass-app-desktop) - A desktop app for PearPass, a password manager
- [@tetherto/pearpass-lib-vault](https://github.com/tetherto/pearpass-lib-vault) - A library for managing password vaults
- [@tetherto/tether-dev-docs](https://github.com/tetherto/tether-dev-docs) - Documentations and guides for developers

## License

This project is licensed under the Apache License, Version 2.0. See the [LICENSE](./LICENSE) file for details.k