<script>
    import axios from 'axios';
    import { push } from 'svelte-spa-router';
    let first_name = '',
        last_name = '',
        email = '',
        password = '',
        password_confirm = '';
    $: submit = async () => {
        await axios.post('http://localhost:5500/api/register', {
            first_name: first_name,
            last_name: last_name,
            email: email,
            password: password,
            password_confirm: password_confirm,
        });
        await push('/login');
    };
</script>

<main class="form-signin">
    <form on:submit|preventDefault={submit}>
        <h1 class="h3 mb-3 fw-normal">Please Register</h1>
        <div class="form-floating">
            <input
                bind:value={first_name}
                type="text"
                class="form-control"
                placeholder="First Name"
            />
            <label>First Name</label>
        </div>
        <div class="form-floating">
            <input
                bind:value={last_name}
                type="text"
                class="form-control"
                placeholder="Last Name"
            />
            <label>Last Name</label>
        </div>
        <div class="form-floating">
            <input
                bind:value={email}
                type="email"
                class="form-control"
                placeholder="name@example.com"
            />
            <label>Email address</label>
        </div>
        <div class="form-floating">
            <input
                bind:value={password}
                type="password"
                class="form-control"
                placeholder="Password"
            />
            <label>Password</label>
        </div>
        <div class="form-floating">
            <input
                bind:value={password_confirm}
                type="password"
                class="form-control"
                placeholder="Password Confirm"
            />
            <label>Password Confirm</label>
        </div>

        <div class="checkbox mb-3" />
        <button class="w-100 btn btn-lg btn-primary" type="submit"
            >Submit</button
        >
    </form>
</main>
