<script>
  let contactInfo = {
    firstname: '',
    lastname: '',
    email: '',
    password: '',
  }

  let contactInfoValidation = {
    firstname: 'valid',
    lastname: 'valid',
    email: 'valid',
    password: 'valid',
  }

  let errorMessage = {
    firstname: '',
    lastname: '',
    email: '',
    password: '',
  }

  let emptyMessage = {
    firstname: 'First Name cannot be empty',
    lastname: 'Last Name cannot be empty',
    email: 'Email cannot be empty',
    password: 'Password cannot be empty',
  }

  // Validate email
  const validRegex = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/
  $: {
    let emailValidation = contactInfo.email.match(validRegex)
    if (!emailValidation && contactInfo.email.length > 0) {
      errorMessage.email = 'Look like this is not an email'
      contactInfoValidation.email = 'invalid'
    } else {
      errorMessage.email = ''
      contactInfoValidation.email = 'valid'
    }
  }

  // Validate password
  const passRegex = /^(?=.*\d)(?=.*[a-z])(?=.*[A-Z]).{6,20}$/
  $: {
    let passwordValidation = contactInfo.password.match(passRegex)
    if (!passwordValidation && contactInfo.password.length > 0) {
      errorMessage.password =
        'Password must be 6 to 20 characters which contain at least one numeric digit, one uppercase and one lowercase letter'
      contactInfoValidation.password = 'invalid'
    } else {
      errorMessage.password = ''
      contactInfoValidation.password = 'valid'
    }
  }

  // Validate form when submit
  const handleSubmit = () => {
    let valid = true
    for (const key in contactInfo) {
      if (Object.hasOwnProperty.call(contactInfo, key)) {
        if (contactInfo[key].length < 1) {
          errorMessage[key] = `${emptyMessage[key]}`
          contactInfoValidation[key] = 'invalid'
          valid = false
        } else {
          errorMessage[key] = ''
          contactInfoValidation[key] = 'valid'
          valid = true
        }
      }
    }
    let emailValidation = contactInfo.email.match(validRegex)
    if (!emailValidation && contactInfo.email.length > 0) {
      errorMessage.email = 'Look like this is not an email'
      contactInfoValidation.email = 'invalid'
      valid = false
    }

    let passwordValidation = contactInfo.password.match(validRegex)
    if (!passwordValidation && contactInfo.email.length > 0) {
      errorMessage.password =
        'Password must be 6 to 20 characters which contain at least one numeric digit, one uppercase and one lowercase letter'
      contactInfoValidation.password = 'invalid'
      valid = false
    }

    valid ? console.log('sign up success') : console.log('error')
  }
</script>

<div class="cta">
  <h2 class="cta__text">
    <span class="highlight">Try it free 7 days</span> then $20/mo. thereafter
  </h2>
  <form on:submit|preventDefault={handleSubmit} class="form">
    <div class="form__field">
      <label for="firstName" class="visually-hidden">First Name</label>
      <input
        data-state={contactInfoValidation.firstname}
        type="text"
        id="firstName"
        placeholder="First Name"
        bind:value={contactInfo.firstname}
      />
      <p class="error-message">{errorMessage.firstname}</p>
      <svg
        class:hide={contactInfoValidation.firstname === 'valid'}
        width="24"
        height="24"
        xmlns="http://www.w3.org/2000/svg"
        ><g fill="none" fill-rule="evenodd"
          ><circle fill="#FF7979" cx="12" cy="12" r="12" /><rect
            fill="#FFF"
            x="11"
            y="6"
            width="2"
            height="9"
            rx="1"
          /><rect fill="#FFF" x="11" y="17" width="2" height="2" rx="1" /></g
        ></svg
      >
    </div>
    <div class="form__field">
      <label for="lastName" class="visually-hidden">Last Name</label>
      <input
        data-state={contactInfoValidation.lastname}
        type="text"
        id="lastName"
        placeholder="Last Name"
        bind:value={contactInfo.lastname}
      />
      <p class="error-message">{errorMessage.lastname}</p>
      <svg
        class:hide={contactInfoValidation.lastname === 'valid'}
        width="24"
        height="24"
        xmlns="http://www.w3.org/2000/svg"
        ><g fill="none" fill-rule="evenodd"
          ><circle fill="#FF7979" cx="12" cy="12" r="12" /><rect
            fill="#FFF"
            x="11"
            y="6"
            width="2"
            height="9"
            rx="1"
          /><rect fill="#FFF" x="11" y="17" width="2" height="2" rx="1" /></g
        ></svg
      >
    </div>
    <div class="form__field email">
      <label for="email" class="visually-hidden">Email Address</label>
      <input
        data-state={contactInfoValidation.email}
        type="email"
        id="email"
        placeholder={contactInfoValidation.email === 'valid'
          ? 'Email Address'
          : 'email@example.com'}
        bind:value={contactInfo.email}
      />
      <p class="error-message">{errorMessage.email}</p>
      <svg
        class:hide={contactInfoValidation.email === 'valid'}
        width="24"
        height="24"
        xmlns="http://www.w3.org/2000/svg"
        ><g fill="none" fill-rule="evenodd"
          ><circle fill="#FF7979" cx="12" cy="12" r="12" /><rect
            fill="#FFF"
            x="11"
            y="6"
            width="2"
            height="9"
            rx="1"
          /><rect fill="#FFF" x="11" y="17" width="2" height="2" rx="1" /></g
        ></svg
      >
    </div>
    <div class="form__field">
      <label for="password" class="visually-hidden">Password</label>
      <input
        data-state={contactInfoValidation.password}
        type="password"
        id="password"
        placeholder="Password"
        bind:value={contactInfo.password}
      />
      <p class="error-message">{errorMessage.password}</p>
      <svg
        class:hide={contactInfoValidation.password === 'valid'}
        width="24"
        height="24"
        xmlns="http://www.w3.org/2000/svg"
        ><g fill="none" fill-rule="evenodd"
          ><circle fill="#FF7979" cx="12" cy="12" r="12" /><rect
            fill="#FFF"
            x="11"
            y="6"
            width="2"
            height="9"
            rx="1"
          /><rect fill="#FFF" x="11" y="17" width="2" height="2" rx="1" /></g
        ></svg
      >
    </div>
    <button class="form__btn">Claim your free trial</button>
    <p class="term-service">
      By clicking the button, you are agreeing to our <span
        >Terms and Services</span
      >
    </p>
  </form>
</div>

<style>
  /* Reset input width */
  input {
    width: 100%;
  }

  /* Style call to action promotion */
  .cta {
    display: flex;
    flex-direction: column;
    gap: 1.5em;
  }

  .cta__text {
    color: var(--clr-neutral-0);
    font-weight: var(--fw-regular);
    font-size: 1em;
    background-color: var(--clr-blue);
    text-align: center;
    border-radius: 12px;
    box-shadow: 0 8px var(--clr-neutral-600-25);
    padding: 1.5em 3em;
  }

  .highlight {
    font-weight: var(--fw-semibold);
  }

  /* Style the form */
  .form {
    background-color: var(--clr-neutral-0);
    display: flex;
    flex-direction: column;
    align-items: stretch;
    padding: 2em;
    gap: 1em;
    border-radius: 12px;
    position: relative;
  }

  /* Form field */
  .form__field {
    position: relative;
    display: flex;
    flex-direction: column;
  }

  .form__field input {
    padding: 0.75em 1em;
    border: 1px solid var(--clr-neutral-600-25);
    border-radius: 6px;
  }

  /* Form field error styling */
  .form__field input[data-state='invalid'] {
    border: 2px solid var(--clr-red);
  }

  .form__field input[data-state='invalid']::placeholder {
    opacity: 0;
  }
  .form__field.email input[data-state='invalid']::placeholder {
    opacity: 1;
    color: var(--clr-red);
  }

  .form__field input::placeholder {
    color: var(--clr-neutral-600-);
    font-weight: var(--fw-medium);
    opacity: 0.5;
    font-size: 0.9em;
  }

  .form__field svg {
    position: absolute;
    right: 0;
    top: 0;
    transform-origin: 0 0;
    transform: translateX(-50%) translateY(60%);
  }

  .form__field svg.hide {
    display: none;
  }

  .form__btn {
    cursor: pointer;
    text-transform: uppercase;
    text-align: center;
    border: none;
    border-radius: 6px;
    background-color: var(--clr-green);
    color: var(--clr-neutral-0);
    font-weight: var(--fw-medium);
    padding: 1em 0;
    box-shadow: 0 4px var(--clr-darker-green);
  }

  .form__btn:hover {
    opacity: 0.75;
  }

  .error-message {
    color: var(--clr-red);
    text-align: end;
    font-size: 0.8em;
    margin-top: 0.2em;
  }

  .term-service {
    font-size: 0.75em;
    text-align: center;
    color: var(--clr-neutral-600-50);
  }

  .term-service span {
    font-weight: var(--fw-bold);
    color: var(--clr-red);
  }

  @media (min-width: 36rem) {
    .form__field input {
      padding: 1em 2em;
    }

    .form__field svg {
      transform: translateX(-50%) translateY(70%);
    }
  }
</style>
