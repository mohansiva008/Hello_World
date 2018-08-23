# Hello_World
<!DOCTYPE html>
<html>
<style>

</style>
<body>
    <fieldset id="normal">
        <form method="POST" id="form0" action="/login">
            <legend>Sign in</legend>

            <div>
                <label for="userName">Username:</label>
                <input type="text" id="username" name="username" required placeholder="Enter username"/>
            </div>

            <div>
                <label for="password">Password:</label>
                <input type="password" id="password" name="password" required placeholder="8 characters minimum" />
            </div>

            <button type="submit" value="Sign in" onclick= "authverify()">Sign In</button>
        </form>
    </fieldset>
    <fieldset id="error">
        <form id="errorform" method="POST" action="/login">
            <h2>You have entered an invalid username or password</h2>
        </form>
    </fieldset> 
    <script>
        document.getElementById('error').style.display = 'none';
        document.getElementById('normal').style.display = 'block';
        var logincount = 3;
        function authverify() {
            
            var usernamevar = document.getElementById('username').value;
            console.log('username..'+usernamevar);
            var passvar = document.getElementById('password').value;
            console.log('passsword...'+passvar);
            
            var authmap = new Map();
            authmap.set('Vishnu', 'pass');
            console.log('authmap..',authmap);
            
            if ((usernamevar != null) && (passvar != null)) {
                console.log('Mike 1');
                if(authmap.has(usernamevar)) {
                    console.log(authmap.get(usernamevar));
                    console.log(passvar);
                    if (authmap.get(usernamevar) == passvar) {
                        console.log('You are authenticated');
                        alert('Login Successfully');                        
                    }
                    else {
                        alert('You have entered an invalid username or password');
                        document.getElementById('error').style.display = 'block';
                        document.getElementById('normal').style.display = 'none';
                        window.location.href = 'localhost:8880/html';
                        console.log('After the change link');
                        if (logincount > 0) {
                            logincount = logincount- 1;
                        }
                        else {
                            alert('Sorry, Your have reached the login attempt limit. So please try again after few minutes');
                        }
                    }
                }
            }               
        }
    </script>
</body>
</html>
