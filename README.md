# Sign-In-App1
To create a app to signin and get all accounts stored
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>My First App</title>
  <style>
    body { font-family: Arial, sans-serif; background: #f4f4f4; padding: 30px; }
    .container { max-width: 400px; margin: auto; padding: 20px; background: white; border-radius: 10px; box-shadow: 0 0 10px #ccc; }
    input, button { width: 100%; padding: 10px; margin: 8px 0; border-radius: 5px; border: 1px solid #ddd; }
    button { background: #007bff; color: white; border: none; cursor: pointer; }
    button:hover { background: #0056b3; }
    .hidden { display: none; }
  </style>
</head>
<body>

<div class="container" id="signup">
  <h2>Signup</h2>
  <input type="text" id="signupEmail" placeholder="Enter Email">
  <input type="password" id="signupPassword" placeholder="Enter Password">
  <button onclick="signup()">Signup</button>
</div>

<div class="container hidden" id="login">
  <h2>Login</h2>
  <input type="text" id="loginEmail" placeholder="Enter Email">
  <input type="password" id="loginPassword" placeholder="Enter Password">
  <button onclick="login()">Login</button>
</div>

<div class="container hidden" id="dashboard">
  <h2>Welcome to Dashboard 🎉</h2>
  <p id="welcomeUser"></p>
  <button onclick="logout()">Logout</button>
</div>

<script>
  function signup() {
    let email = document.getElementById("signupEmail").value;
    let password = document.getElementById("signupPassword").value;
    if (email && password) {
      localStorage.setItem("userEmail", email);
      localStorage.setItem("userPassword", password);
      alert("Signup successful! Please login.");
      document.getElementById("signup").classList.add("hidden");
      document.getElementById("login").classList.remove("hidden");
    } else {
      alert("Please fill all fields.");
    }
  }

  function login() {
    let email = document.getElementById("loginEmail").value;
    let password = document.getElementById("loginPassword").value;
    let storedEmail = localStorage.getItem("userEmail");
    let storedPassword = localStorage.getItem("userPassword");
    if (email === storedEmail && password === storedPassword) {
      document.getElementById("login").classList.add("hidden");
      document.getElementById("dashboard").classList.remove("hidden");
      document.getElementById("welcomeUser").innerText = "Hello, " + email;
    } else {
      alert("Invalid credentials. Try again!");
    }
  }

  function logout() {
    document.getElementById("dashboard").classList.add("hidden");
    document.getElementById("login").classList.remove("hidden");
  }
</script>

</body>
</html>
