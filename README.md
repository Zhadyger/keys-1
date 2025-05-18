<!DOCTYPE html>
<html lang="ru">
<head>
    <meta charset="UTF-8">
    <title>Анализ видео с Google Video Intelligence API</title>
    <style>
        body {
            font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
            background: #f0f4f8;
            margin: 0; padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
            min-height: 100vh;
        }
        h1 {
            margin-top: 40px;
            color: #2c3e50;
        }
        form {
            margin-top: 30px;
            background: white;
            padding: 20px 30px;
            border-radius: 8px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.1);
        }
        input[type="file"] {
            margin-bottom: 15px;
        }
        input[type="submit"] {
            cursor: pointer;
            background: #3498db;
            border: none;
            padding: 10px 20px;
            color: white;
            font-weight: 600;
            border-radius: 5px;
            transition: background 0.3s ease;
        }
        input[type="submit"]:hover {
            background: #2980b9;
        }
        ul {
            list-style-type: none;
            padding-left: 0;
            margin-top: 20px;
        }
        ul li {
            background: #ecf0f1;
            margin: 5px 0;
            padding: 8px 15px;
            border-radius: 5px;
            font-size: 1.1em;
        }
        video {
            margin-top: 25px;
            border-radius: 8px;
            box-shadow: 0 3px 10px rgba(0,0,0,0.15);
        }
        .container {
            width: 100%;
            max-width: 600px;
            padding: 20px;
        }
    </style>
</head>
<body>
<div class="container">
    <h1>Загрузите видео для анализа</h1>
    <form method="post" enctype="multipart/form-data">
        <input type="file" name="video_file" accept="video/*" required><br>
        <input type="submit" value="Анализировать">
    </form>

    {% if labels %}
        <h2>Обнаруженные метки:</h2>
        <ul>
            {% for label in labels %}
            <li>{{ label }}</li>
            {% endfor %}
        </ul>
        <video width="480" controls>
            <source src="{{ video_url }}" type="video/mp4">
            Ваш браузер не поддерживает видео.
        </video>
    {% endif %}
</div>
</body>
</html>
