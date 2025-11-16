---
layout: default
title: Devlog — State Rise
id: devlog
---

<h1>Devlog</h1>
<div id="devlog-container">
    <p>Загружается...</p>
</div>

<script>
fetch("/data/devlog.json")
    .then(r => r.json())
    .then(entries => {
        const c = document.getElementById("devlog-container");
        c.innerHTML = "";
        entries.forEach(e => {
            c.innerHTML += `
                <h2>${e.title}</h2>
                <small>${e.date}</small>
                <p>${e.text}</p><hr>
            `;
        });
    })
    .catch(() => {
        document.getElementById("devlog-container").innerHTML =
            "<p>Ошибка загрузки.</p>";
    });
</script>
