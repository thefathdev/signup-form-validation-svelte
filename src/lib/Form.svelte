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
</script>

<div class="cta">
  <h2 class="cta__text">
    <span class="highlight">Try it free 7 days</span> then $20/mo. thereafter
  </h2>
  <form on:submit class="form">
    <div class="form__field">
      <label for="firstName" class="visually-hidden">First Name</label>
      <input type="text" id="firstName" placeholder="First Name" />
      <p class="error-message">error</p>
    </div>
    <div class="form__field">
      <label for="lastName" class="visually-hidden">Last Name</label>
      <input type="text" id="lastName" placeholder="Last Name" />
      <p class="error-message">error</p>
    </div>
    <div class="form__field">
      <label for="email" class="visually-hidden">Email Address</label>
      <input type="email" id="email" placeholder="Email Address" />
      <p class="error-message">error</p>
    </div>
    <div class="form__field">
      <label for="password" class="visually-hidden">Password</label>
      <input type="password" id="password" placeholder="Password" />
      <p class="error-message">error</p>
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
  input {
    width: 100%;
  }
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

  .form {
    background-color: var(--clr-neutral-0);
    display: flex;
    flex-direction: column;
    align-items: stretch;
    padding: 2em;
    gap: 1em;
    border-radius: 12px;
  }

  .form__field input {
    padding: 0.75em 1em;
    border: 1px solid var(--clr-neutral-600-25);
    border-radius: 6px;
  }

  .form__field input::placeholder {
    color: var(--clr-neutral-600-);
    font-weight: var(--fw-medium);
    opacity: 0.5;
    font-size: 0.9em;
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
</style>
