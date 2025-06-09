<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>PFKahoot!</title>
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
  <link rel="icon" type="image/png" href="https://cdn.discordapp.com/attachments/1381221101547421729/1381593423361867857/4D40AB28-5CF9-46BC-8F7A-539588E42B5E.png?ex=684814a4&is=6846c324&hm=48ab23511caaa92a58adee20d68366e2f783b45041641dac54e4520d4a262280&">
</head>
<body class="bg-gradient-to-br from-blue-900 to-white min-h-screen flex items-center justify-center p-4">
  <div class="bg-white rounded-2xl shadow-lg p-6 w-full max-w-md" id="loginBox">
    <h1 class="text-3xl font-bold text-center text-blue-700 mb-6">Welcome to PFKahoot!</h1>

    <form onsubmit="login(event)" class="space-y-4">
      <input type="email" id="email" placeholder="E-mail Address" class="w-full px-4 py-2 border rounded" required>
      <input type="password" id="password" placeholder="Password" class="w-full px-4 py-2 border rounded" required>
      <button type="submit" class="w-full bg-blue-600 text-white py-2 rounded hover:bg-blue-700">Sign in</button>
    </form>

    <div class="flex justify-between mt-4 gap-2">
      <button onclick="alert('Google login not available.')" class="w-1/2 flex items-center justify-center gap-2 border rounded py-2">
        <img src="https://www.svgrepo.com/show/475656/google-color.svg" class="w-5 h-5" /> Google
      </button>
      <button onclick="loginWithDiscord()" class="w-1/2 flex items-center justify-center gap-2 border rounded py-2">
        <img src="https://www.svgrepo.com/show/353655/discord-icon.svg" class="w-5 h-5" /> Discord
      </button>
    </div>

    <p class="text-center text-sm mt-4">Don't have an account? <a href="#" class="text-blue-600">Sign up</a></p>
  </div>

  <div id="userInfo" class="hidden text-center">
    <h2 class="text-3xl font-bold text-blue-800">Welcome, <span id="usernameDisplay"></span>!</h2>
    <img id="avatarDisplay" src="" width="100" class="rounded-full my-4"/>
    <p class="text-lg" id="emailDisplay"></p>
    <a href="index.html" class="text-blue-600 mt-6 inline-block">Log out</a>
  </div>

  <script>
    function login(e) {
      e.preventDefault();
      const email = document.getElementById('email').value;
      alert("Logging in with " + email);
    }

    function loginWithDiscord() {
      const redirect = encodeURIComponent("https://a350dreams.github.io/pfkahoot-main/");
      const clientId = "1381612652756861068";
      const scope = "identify email";
      const responseType = "code";

      window.location.href =
        `https://discord.com/oauth2/authorize?client_id=${clientId}&redirect_uri=${redirect}&response_type=${responseType}&scope=${scope}`;
    }

    // When redirected back from Discord
    const params = new URLSearchParams(window.location.search);
    const username = params.get('username');
    const avatar = params.get('avatar');
    const id = params.get('id');
    const email = params.get('email');

    if (username && avatar && id) {
      document.getElementById("loginBox").classList.add("hidden");
      document.getElementById("userInfo").classList.remove("hidden");
      document.getElementById("usernameDisplay").textContent = username;
      document.getElementById("avatarDisplay").src = `https://cdn.discordapp.com/avatars/${id}/${avatar}.png`;
      document.getElementById("emailDisplay").textContent = `Email: ${email || "Unavailable"}`;
    }
  </script>
</body>
</html>
<!-- This code provides a simple login interface for PFKahoot! -->
<!-- It includes email/password login, Google and Discord login options, and displays user info after login. -->
