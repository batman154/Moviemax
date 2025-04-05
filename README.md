# Moviemax
A movie view<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>MovieZone</title>
  <style>
    body {
      margin: 0;
      font-family: 'Segoe UI', sans-serif;
      background-color: #0f0f0f;
      color: #fff;
      padding: 20px;
    }

    header {
      text-align: center;
      padding: 20px 0;
    }

    h1 {
      font-size: 2.5rem;
      color: #ff3c00;
    }

    #searchInput {
      width: 100%;
      max-width: 400px;
      padding: 10px;
      font-size: 1rem;
      border: none;
      border-radius: 8px;
      margin-top: 15px;
      text-align: center;
    }

    .movies {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
      gap: 20px;
      margin-top: 30px;
    }

    .movie-card {
      background-color: #1a1a1a;
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0 0 15px rgba(255, 60, 0, 0.2);
      transition: transform 0.3s;
    }

    .movie-card:hover {
      transform: scale(1.03);
    }

    .movie-card img {
      width: 100%;
      height: 350px;
      object-fit: cover;
    }

    .movie-content {
      padding: 15px;
    }

    .movie-content h2 {
      font-size: 1.4rem;
      margin: 0 0 10px;
    }

    .movie-content p {
      font-size: 0.95rem;
      color: #bbb;
    }

    iframe {
      width: 100%;
      height: 200px;
      border: none;
      border-radius: 10px;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <header>
    <h1>MovieZone</h1>
    <p>Explore Top Movies with Trailers & Info</p>
    <input type="text" id="searchInput" placeholder="Search movies...">
  </header>

  <div class="movies" id="movieContainer"></div>

  <script>
    const movies = [
      {
        title: "KGF Chapter 2",
        year: "2022",
        genre: "Action/Drama",
        description: "Rocky takes charge as the king of Kolar Gold Fields.",
        image: "https://upload.wikimedia.org/wikipedia/en/6/6e/K.G.F_Chapter_2.jpg",
        trailer: "https://www.youtube.com/embed/JKa05nyUmuQ"
      },
      {
        title: "Pushpa: The Rise",
        year: "2021",
        genre: "Action/Crime",
        description: "Pushpa Raj rises from a worker to a sandalwood don.",
        image: "https://upload.wikimedia.org/wikipedia/en/7/72/Pushpa_-_The_Rise_%282021_film%29.jpg",
        trailer: "https://www.youtube.com/embed/Q1NKMPhP8PY"
      },
      {
        title: "RRR",
        year: "2022",
        genre: "Action/Adventure",
        description: "A fictional story about two legendary freedom fighters.",
        image: "https://upload.wikimedia.org/wikipedia/en/d/d7/RRR_Poster.jpg",
        trailer: "https://www.youtube.com/embed/f_vbAtFSEc0"
      }
    ];

    const container = document.getElementById("movieContainer");
    const searchInput = document.getElementById("searchInput");

    function displayMovies(movieList) {
      container.innerHTML = "";
      movieList.forEach(movie => {
        const card = document.createElement("div");
        card.className = "movie-card";
        card.innerHTML = `
          <img src="${movie.image}" alt="${movie.title} Poster" />
          <div class="movie-content">
            <h2>${movie.title}</h2>
            <p>${movie.year} · ${movie.genre}</p>
            <p>${movie.description}</p>
            <iframe src="${movie.trailer}" allowfullscreen></iframe>
          </div>
        `;
        container.appendChild(card);
      });
    }

    searchInput.addEventListener("input", () => {
      const keyword = searchInput.value.toLowerCase();
      const filtered = movies.filter(movie =>
        movie.title.toLowerCase().includes(keyword)
      );
      displayMovies(filtered);
    });

    // Display all movies initially
    displayMovies(movies);
  </script>
</body>
</html>
