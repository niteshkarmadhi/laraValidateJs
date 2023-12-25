# LaraValidateJS 

LaraValidateJS brings the robust and intuitive validation techniques of Laravel to JavaScript environments. Leveraging the power of ValidatorJS npm internally, this package offers a seamless and familiar validation experience for JavaScript developers, reminiscent of Laravel's validation methods.

With LaraValidateJS, effortlessly implement validation rules similar to Laravel's syntax, ensuring your data meets predefined criteria before proceeding. This package allows you to define rules for various data types, perform custom validations, and handle complex validation scenarios with ease.

## Installation

### Using npm

```bash
npm install laravalidatejs
```

### Using yarn

```bash
yarn add laravalidatejs
```

### Browserify

```js
// ES6
import Validators from 'laravalidatejs'
```

### Basic Usage

```js
      const rules = {
        email: 'required|email|max:10|min:20'
      }

      const [formState, setFormState] = useState({
        email: ""
      });

       const handleSubmit = (formData) => {
          // apply your logic
        };

      <Validators formData={formState} rules={rules}>
				{({ onSubmit, errors, resetValidation }) => {
					return (
						<form>
							<input
								name="email"
								label="Email Address"
								type="email"
								value={formState?.email}
								onChange={onChange}
								placeholder="Yourname@email.com"
							/>
							{/* Add other form inputs */}
							<button type="button" onClick={() => onSubmit(handleSubmit)}>
								Submit
							</button>
							{/* Display validation errors if any */}
							{errors && errors.email && (
								<p style={{ color: 'red' }}>{errors.email[0]}</p>
							)}
							{/* Add more error displays if needed */}
						</form>
					);
				}}
			</Validators>
```

__formData__ {Object} - This prop contains the current state of the form data. It's typically an object that holds various field values that a user has entered or modified within a form

__rules__ {Object} - The rules prop defines the validation criteria for each form field. It's often an object containing rules that specify how the data in each field should be validated. These rules typically include conditions such as required fields, minimum and maximum length, valid email format, numeric values.

__onSubmit__ {Function} - The onSubmit is a callback prop where we define the original function (handleSubmit) responsible for executing actions like API calls or other necessary tasks. After defining this function, when we click the submit button on the form, it triggers a validation process.

During this validation process, if the form data meets all the validation criteria without any errors, the onSubmit function proceeds to call the handleSubmit function that we provided as a parameter. This means that if everything is correct according to the validation rules, the handleSubmit function is executed.

However, if there are any validation errors found in the form data based on the specified rules, the onSubmit function won’t call the handleSubmit function. Instead, it captures these validation errors and stores them in the errors variable. This allows us to handle and display these errors to the user, indicating what specific corrections need to be made before the form can be successfully submitted.

__errors__ {Object} - we will receive all the validation errors in a format similar to the example below:



#### Example

```js
let errors = {
  email: [
    'Email format is invalid.',
    'Email is required.',
  ]
};
```

## Options

| Property | Type | Description |
|----------|------|-------------|
| setErrors | function | put here custom validation error comes from backend like above format. |

#### Here are some custom rules that do not exist in the validatorjs library.
````
  let rules = {
    image: 'mimes:png,jpg,jpeg,svg,webp|max_file_size:1048576|min_file_size:1048576',
    password: "required|password",
	  confirm_password: "required|confirm_password",
  }
````

#### Note
if you want to know about the validation rules then check validatorjs npm library