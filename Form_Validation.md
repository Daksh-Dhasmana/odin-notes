### Form Validation
- They help protect the backend servers from incorrect or incomplete information.
- They also tell/guide the user to enter correct or full information.

## Require Validation
- This helps from getting empty information.
- They tell user to enter the info. if they left it.
- It will ensure that specific fields have been filled before submitting the form.
- `<input type="text" required>`.

## Text Length Validation
- This helps to restrict the length of characters(including numbers) entered by user.
- `minlength` and `maxlegth`. They are self explanatory.

## Number Length Validation
- This helps to restrict the range of numbers entered by user.
- eg: `<input type="number" min=18 max=100>` 20 yes, 5 no.

## Pattern Validation
- It helps to ensure we get a correct pattern
- In IRL application, we use this to check a password, zipcode, credit card number, email-id etc.
- `<input type="text" pattern="(\d{5}([\-]\d{4})?)">`.

## Styling Validation
- `:user-valid`and `:user-invalid` pseudo classes allow form controls to either indicate passed or fail validation.
- IMPORTANT: They need other form validations to work well, like required, min, max.
- `input:user-invalid{border-color:red}`.
