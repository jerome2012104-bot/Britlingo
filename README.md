# Britlingo
https://github.com/DEINNAME/britlingo
<!DOCTYPE html>
<html lang="de">
<head>
  <meta charset="UTF-8" />
  <title>GitHub Helfer – Description & README kopieren</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      max-width: 600px;
      margin: 40px auto;
      background: #f0f4f8;
      padding: 20px;
      border-radius: 10px;
      text-align: center;
      color: #222;
    }
    h1 {
      color: #0366d6;
    }
    button {
      margin: 12px;
      padding: 12px 24px;
      font-size: 16px;
      cursor: pointer;
      border: none;
      border-radius: 8px;
      background-color: #28a745;
      color: white;
      transition: background-color 0.3s ease;
    }
    button:hover {
      background-color: #1e7e34;
    }
    #feedback {
      margin-top: 20px;
      font-weight: bold;
      color: #155724;
    }
    textarea {
      width: 100%;
      height: 200px;
      margin-top: 20px;
      font-family: monospace;
      font-size: 14px;
      padding: 10px;
      border-radius: 8px;
      border: 1px solid #ccc;
      resize: vertical;
    }
  </style>
</head>
<body>

  <h1>GitHub Helfer</h1>
  <p>Einfach Klick auf einen Button, um Text in die Zwischenablage zu kopieren.</p>

  <button onclick="copyDescription()">Beschreibung kopieren</button>
  <button onclick="copyReadme()">README.md Vorlage kopieren</button>

  <div id="feedback"></div>

  <textarea id="readmePreview" readonly></textarea>

  <script>
    const descriptionText = "Mini-Web-App zum Lernen von britischem Englisch mit Multiple-Choice-Quiz";

    const readmeText = `# BritLingo

Eine Mini-Web-App zum Lernen von britischem Englisch mit Multiple-Choice-Quiz.

## Features

- Interaktives Quiz mit britischen Vokabeln und Ausdrücken  
- Einfaches Interface, ideal zum Sprachenlernen  
- Direkt im Browser nutzbar, keine Installation notwendig

## Installation

Einfach die Datei \`britlingo.html\` im Browser öffnen.

## Nutzung

Beantworte die Fragen und verbessere dein Englisch!

## Lizenz

MIT License

---

*Dieses Projekt wurde mit ChatGPT erstellt.*`;

    const feedback = document.getElementById("feedback");
    const readmePreview = document.getElementById("readmePreview");

    function copyDescription() {
      navigator.clipboard.writeText(descriptionText).then(() => {
        feedback.textContent = "Beschreibung wurde kopiert!";
        feedback.style.color = "#155724";
      }).catch(() => {
        feedback.textContent = "Kopieren fehlgeschlagen. Bitte manuell kopieren.";
        feedback.style.color = "#721c24";
      });
    }

    function copyReadme() {
      navigator.clipboard.writeText(readmeText).then(() => {
        feedback.textContent = "README.md Vorlage wurde kopiert!";
        feedback.style.color = "#155724";
        readmePreview.value = readmeText;
      }).catch(() => {
        feedback.textContent = "Kopieren fehlgeschlagen. Bitte manuell kopieren.";
        feedback.style.color = "#721c24";
      });
    }
  </script>

</body>
</html>
