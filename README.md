# react-light-form
The React Light Form component for getting state from a plain form. It's super easy to use and it's lightweight! And has incredible type safety!

## Usage
#### Simple example
Preaty concise, yeah?
```tsx
import Form, { FormState } from "react-light-form"

enum FormInputs {
  passwordOld = "password_old",
  password = "password",
  passwordConfirm = "password_confirm"
}

function ProfilePersonalPasswordChange() {
  const { mutate } = useMutation(postCabinetUsersPassword)
  async function onSubmit(state: FormState<FormInputs, string>) { // Gather values from FormInputs and type them as `string`
    const { error } = await mutate(state.values) // Values are `password_old`, `password`, `password_confirm`
    if (error) return

    // ...
  }
  return (
    <>
      <h5 className="heading">Password Update</h5>
      <Form onSubmit={onSubmit}>
        <input name={FormInputs.passwordOld} placeholder="Current password" />
        <input name={FormInputs.password} placeholder="New password" />
        <input name={FormInputs.passwordConfirm} placeholder="Confirm new password" />
        <button type="submit">Update</button>
      </Form>
    </>
  )
}

export default ProfilePersonalPasswordChange
```
