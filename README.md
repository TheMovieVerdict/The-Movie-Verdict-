<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Top 250 Movies</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #1a1a1a;
            color: #fff;
            text-align: center;
            margin: 0;
        }
        header {
            padding: 20px;
            background-color: #ff9900;
        }
        input {
            padding: 10px;
            width: 50%;
            font-size: 16px;
        }
        table {
            width: 80%;
            margin: 20px auto;
            border-collapse: collapse;
        }
        th, td {
            padding: 10px;
            border: 1px solid #fff;
        }
        th {
            background-color: #ff9900;
        }
        tr:nth-child(even) {
            background-color: #333;
        }
    </style>
</head>
<body>
    <header>
        <h1>Top 250 Movies</h1>
        <input type="text" id="searchBar" placeholder="Search movies...">
    </header>

    <main>
        <table>
            <thead>
                <tr>
                    <th>Rank</th>
                    <th>Movie</th>
                    <th>Year</th>
                    <th>Rating</th>
                </tr>
            </thead>
            <tbody id="movieTable"></tbody>
        </table>
    </main>

    <script>
        document.addEventListener("DOMContentLoaded", function () {
            const movies = [
                { rank: 1, title: "The Shawshank Redemption", year: 1994, rating: 9.3 },
                { rank: 2, title: "The Godfather", year: 1972, rating: 9.2 },
                { rank: 3, title: "The Dark Knight", year: 2008, rating: 9.0 },
                { rank: 4, title: "The Godfather Part II", year: 1974, rating: 9.0 },
                { rank: 5, title: "12 Angry Men", year: 1957, rating: 9.0 },
                { rank: 6, title: "Schindler's List", year: 1993, rating: 8.9 },
                { rank: 7, title: "The Lord of the Rings: The Return of the King", year: 2003, rating: 8.9 },
                { rank: 8, title: "Pulp Fiction", year: 1994, rating: 8.9 },
                { rank: 9, title: "The Lord of the Rings: The Fellowship of the Ring", year: 2001, rating: 8.8 },
                { rank: 10, title: "Fight Club", year: 1999, rating: 8.8 }
            ];

            const tableBody = document.getElementById("movieTable");

            function displayMovies(movieList) {
                tableBody.innerHTML = "";
                movieList.forEach(movie => {
                    const row = `<tr>
                        <td>${movie.rank}</td>
                        <td>${movie.title}</td>
                        <td>${movie.year}</td>
                        <td>${movie.rating}</td>
                    </tr>`;
                    tableBody.innerHTML += row;
                });
            }

            displayMovies(movies);

            document.getElementById("searchBar").addEventListener("input", function (event) {
                const searchText = event.target.value.toLowerCase();
                const filteredMovies = movies.filter(movie =>
                    movie.title.toLowerCase().includes(searchText)
                );
                displayMovies(filteredMovies);
            });
        });
    </script>
</body>
</html>
