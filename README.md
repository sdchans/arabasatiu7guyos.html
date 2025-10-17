<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8" />
  <title>Katman Listesi - Sürükle Bırak</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      padding: 30px;
      background-color: #f1f1f1;
      text-align: center;
    }

    h1 {
      margin-bottom: 20px;
    }

    ul {
      list-style: none;
      padding: 0;
      width: 300px;
      margin: auto;
    }

    li {
      padding: 15px;
      margin: 5px;
      background-color: #ffffff;
      border: 2px solid #ccc;
      cursor: move;
      font-size: 18px;
      transition: 0.2s;
    }

    li.dragging {
      opacity: 0.5;
      background-color: #d1ecf1;
    }
  </style>
</head>
<body>

  <h1>🧩 Katman Sıralaması</h1>
  <p>Sürükleyerek sıralamayı değiştir</p>

  <ul id="katmanListesi">
    <li draggable="true">Hepsi O Valorantın suçu</li>
    <li draggable="true">Kara Panter</li>
    <li draggable="true">Helal Olsun Hikmet</li>
    <li draggable="true">Mehmet</li>
    <li draggable="true">Uçan Adam</li>
    <li draggable="true">67</li>
    <li draggable="true">Çupa çups</li>
    <li draggable="true">929992</li>
    <li draggable="true">Maymun Hikmet</li>
    <li draggable="true">Sen benim üzümlü kekim</li>
    <li draggable="true">Osur Hikmet Bokuk hikmet</li>
    <li draggable="true">hikmetin 90 a giden topunu kurtardikten sonra serdar</li>
    <li draggable="true">gongidi</li>
    <li draggable="true">thomas shelby</li>
  </ul>

  <script>
    const listItems = document.querySelectorAll("#katmanListesi li");
    let draggingItem = null;

    listItems.forEach(item => {
      item.addEventListener("dragstart", () => {
        draggingItem = item;
        item.classList.add("dragging");
      });

      item.addEventListener("dragend", () => {
        draggingItem = null;
        item.classList.remove("dragging");
      });

      item.addEventListener("dragover", e => {
        e.preventDefault();
        const bounding = item.getBoundingClientRect();
        const offset = e.clientY - bounding.top + bounding.height / 2;
        const list = document.getElementById("katmanListesi");
        if (offset > bounding.height / 2) {
          list.insertBefore(draggingItem, item.nextSibling);
        } else {
          list.insertBefore(draggingItem, item);
        }
      });
    });
  </script>

</body>
</html>
