# Download-duniya
My download website
<!DOCTYPE html><html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Download Duniya</title>
  <style>
    body {
      margin: 0;
      font-family: Arial, sans-serif;
      background: #f3f6fb;
      color: #222;
    }
    header {
      background: #155eef;
      color: white;
      text-align: center;
      padding: 28px 12px;
    }
    .search {
      display: block;
      width: 85%;
      max-width: 450px;
      margin: 25px auto;
      padding: 13px;
      border: 1px solid #ccc;
      border-radius: 8px;
      font-size: 16px;
    }
    .categories {
      text-align: center;
      margin: 15px;
    }
    button {
      border: none;
      border-radius: 6px;
      padding: 10px 14px;
      margin: 4px;
      background: #155eef;
      color: white;
      cursor: pointer;
    }
    .files {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 15px;
      padding: 15px;
    }
    .card {
      background: white;
      padding: 18px;
      border-radius: 10px;
      box-shadow: 0 2px 8px #ddd;
    }
    .download {
      display: inline-block;
      background: #14804a;
      color: white;
      padding: 10px 14px;
      border-radius: 5px;
      text-decoration: none;
    }
  </style>
</head>
<body>
  <header>
    <h1>📥 Download Duniya</h1>
    <p>Find and download your useful files</p>
  </header><input
class="search"
id="search"
type="search"
placeholder="Search files..."
aria-label="Search files"

«»

  <div class="categories">
    <button onclick="showCategory('All')">All</button>
    <button onclick="showCategory('PDF')">PDF & Notes</button>
    <button onclick="showCategory('Apps')">Apps</button>
    <button onclick="showCategory('Software')">Software</button>
  </div>  <main class="files" id="files"></main>  <script>
    const fileList = [
      {
        name: "Sample PDF Notes",
        category: "PDF",
        description: "Example study notes"
      },
      {
        name: "Sample Android App",
        category: "Apps",
        description: "Example app listing"
      },
      {
        name: "Sample Software",
        category: "Software",
        description: "Example software listing"
      }
    ];

    function renderFiles(category = "All", query = "") {
      const container = document.getElementById("files");
      const filtered = fileList.filter(file =>
        (category === "All" || file.category === category) &&
        file.name.toLowerCase().includes(query.toLowerCase())
      );

      container.innerHTML = "";

      filtered.forEach(file => {
        const card = document.createElement("article");
        card.className = "card";

        const title = document.createElement("h3");
        title.textContent = file.name;

        const description = document.createElement("p");
        description.textContent = file.description;

        const type = document.createElement("p");
        type.textContent = "Category: " + file.category;

        card.append(title, description, type);
        container.appendChild(card);
      });

      if (filtered.length === 0) {
        container.textContent = "No files found.";
      }
    }

    function showCategory(category) {
      renderFiles(category, document.getElementById("search").value);
    }

    document.getElementById("search").addEventListener("input", event => {
      renderFiles("All", event.target.value);
    });

    renderFiles();
  </script></body>
</html>
