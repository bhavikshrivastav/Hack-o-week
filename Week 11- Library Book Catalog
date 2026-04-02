<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Library Catalog</title>

    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: Arial, sans-serif;
        }

        body {
            height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;

            background: url('https://images.unsplash.com/photo-1521587760476-6c12a4b040da') no-repeat center/cover;
        }

        /* Dark overlay */
        body::before {
            content: "";
            position: absolute;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.6);
            top: 0;
            left: 0;
        }

        .container {
            position: relative;
            width: 500px; /* increased size */
            padding: 30px;

             background: rgba(50, 50, 50, 0.7);
    color: white;
    backdrop-filter: blur(8px);
            border-radius: 15px;
            box-shadow: 0 10px 25px rgba(0,0,0,0.5);

            text-align: center;
            z-index: 1;
        }

        h2 {
            margin-bottom: 15px;
        }

        input {
            width: 90%;
            padding: 10px;
            margin: 10px 0;
            border-radius: 8px;
            border: 1px solid #ccc;
            font-size: 16px;
        }

        button {
            padding: 10px 15px;
            margin: 5px;
            border: none;
            border-radius: 8px;
            background: #333;
            color: white;
            cursor: pointer;
            transition: 0.3s;
        }

        button:hover {
            background: #555;
            transform: scale(1.05);
        }

        ul {
            margin-top: 15px;
            text-align: left;
            max-height: 150px;
            overflow-y: auto;
        }

        li {
            padding: 5px;
            border-bottom: 1px solid #ddd;
        }
    </style>
</head>
<body>

<div class="container">
    <h2> Library Catalog</h2>

    <input type="text" id="title" placeholder="Enter book title">

    <br>

    <button onclick="addBook()">Add</button>
    <button onclick="removeBook()">Remove</button>
    <button onclick="searchBook()">Search</button>

    <h3>Books List</h3>
    <ul id="bookList"></ul>
</div>

<script>
    const MAX_SIZE = 5;
    let books = [];
    let count = 0;

    function addBook() {
        let title = document.getElementById("title").value.trim();

        if (title === "") {
            alert("Enter a book title");
            return;
        }

        if (count >= MAX_SIZE) {
            alert("Library is full!");
            return;
        }

        books[count++] = title;
        displayBooks();
    }

    function removeBook() {
        let title = document.getElementById("title").value.trim();
        let index = -1;

        for (let i = 0; i < count; i++) {
            if (books[i].toLowerCase() === title.toLowerCase()) {
                index = i;
                break;
            }
        }

        if (index === -1) {
            alert("Book not found");
            return;
        }

        for (let i = index; i < count - 1; i++) {
            books[i] = books[i + 1];
        }

        books.pop();
        count--;

        displayBooks();
    }

    function searchBook() {
        let title = document.getElementById("title").value.trim();

        for (let i = 0; i < count; i++) {
            if (books[i].toLowerCase() === title.toLowerCase()) {
                alert("Book found: " + books[i]);
                return;
            }
        }

        alert("Book not found");
    }

    function displayBooks() {
        let list = document.getElementById("bookList");
        list.innerHTML = "";

        for (let i = 0; i < count; i++) {
            let li = document.createElement("li");
            li.textContent = books[i];
            list.appendChild(li);
        }
    }
</script>

</body>
</html>
