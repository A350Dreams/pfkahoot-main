<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>PFKahoot! - Home</title>
  <link href="https://cdn.jsdelivr.net/npm/tailwindcss@2.2.19/dist/tailwind.min.css" rel="stylesheet">
</head>
<body class="bg-gradient-to-br from-blue-900 to-blue-100 min-h-screen text-white flex items-center justify-center p-4">

  <div class="bg-white text-gray-800 rounded-2xl shadow-xl p-8 max-w-3xl w-full">
    <div class="text-center">
      <h1 class="text-4xl font-extrabold text-blue-700 mb-2">Welcome to PFKahoot!</h1>
      <p class="text-lg text-gray-600">A multiplayer quiz game for Project Flight. </p>
    </div>

    <div id="userInfo" class="text-center mt-6 hidden">
      <p class="text-xl font-semibold">Hello, <span id="usernameDisplay"></span> 👋</p>
      <img id="avatarDisplay" src="" alt="Avatar" class="mx-auto my-4 w-24 h-24 rounded-full border border-blue-500">
    </div>

    <div class="flex flex-col md:flex-row justify-center gap-4 mt-8">
      <button onclick="alert('Create Game not implemented yet')" class="bg-blue-600 hover:bg-blue-700 text-white py-3 px-6 rounded-lg font-semibold shadow">
        ➕ Create a Game
      </button>
      <button onclick="alert('Join Game not implemented yet')" class="bg-green-600 hover:bg-green-700 text-white py-3 px-6 rounded-lg font-semibold shadow">
        🔑 Join a Game
      </button>
    </div>

    <div class="text-center mt-10">
      <p class="text-sm text-gray-500">Not logged in?</p>
      <a href="https://pfkahoot-backend.onrender.com/auth/discord" class="text-blue-600 underline">Log in with Discord</a>
    </div>
  </div>

  <script>
    // Check for user info in query parameters
    const params = new URLSearchParams(window.location.search);
    const username = params.get('username');
    const avatar = params.get('avatar');
    const id = params.get('id');

    if (username && avatar && id) {
      document.getElementById("userInfo").classList.remove("hidden");
      document.getElementById("usernameDisplay").textContent = username;
      document.getElementById("avatarDisplay").src = `https://cdn.discordapp.com/avatars/${id}/${avatar}.png`;
    }
  </script>

</body>
</html>
