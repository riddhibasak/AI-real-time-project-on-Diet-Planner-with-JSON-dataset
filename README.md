<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Personalized Diet and Workout Recommendation</title>
    <link rel="stylesheet" href="{{ url_for('static', filename='styles.css')}}">

    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f7f9fc;
            margin: 0;
            padding: 20px;
        }
        .container {
            max-width: 700px;
            margin: auto;
            padding: 20px;
            background: white;
            box-shadow: 0 4px 8px rgba(0,0,0,0.2);
            border-radius: 8px;
        }
        h2 { color: #4A90E2; }
        label { display: block; margin: 10px 0 5px; font-weight: bold; }
        input, textarea {
            width: 100%; padding: 8px; margin-bottom: 15px;
            border: 1px solid #ccc; border-radius: 4px;
        }
        button {
            width: 100%; padding: 10px;
            background: #4A90E2; color: white;
            border: none; border-radius: 4px;
            font-size: 16px; cursor: pointer;
        }
        button:hover { background: #357ABD; }
        ul { list-style-type: none; padding: 0; }
        li { padding: 5px 0; }
    </style>
</head>
<body>
<div class="container">
    <h2>Personalized Diet & Workout Planner</h2>
    <form action="/recommendations" method="POST">
        <label>Dietary Preferences:</label>
        <input type="text" name="dietary_preferences" placeholder="e.g., vegetarian, non-vegetarian" required>

        <label>Fitness Goals:</label>
        <input type="text" name="fitness_goals" placeholder="e.g., weight loss, muscle gain" required>

        <label>Lifestyle Factors:</label>
        <input type="text" name="lifestyle_factors" placeholder="e.g., active, sedentary" required>

        <label>Dietary Restrictions:</label>
        <input type="text" name="dietary_restrictions" placeholder="e.g., gluten-free, lactose-intolerant">

        <label>Health Conditions:</label>
        <input type="text" name="health_conditions" placeholder="e.g., diabetes, high blood pressure">

        <label>Your Query:</label>
        <textarea name="user_query" placeholder="Describe your goal briefly" required></textarea>

        <button type="submit">Get Recommendations</button>
    </form>
</div>

{% if recommendations %}
<div class="container">
    <h2>Recommendations</h2>
    <h3>Diet Types</h3>
    <ul>{% for diet in recommendations.diet_types %}<li>{{ diet }}</li>{% endfor %}</ul>

    <h3>Workouts</h3>
    <ul>{% for workout in recommendations.workouts %}<li>{{ workout }}</li>{% endfor %}</ul>

    <h3>Breakfast Ideas</h3>
    <ul>{% for bf in recommendations.breakfasts %}<li>{{ bf }}</li>{% endfor %}</ul>

    <h3>Dinner Options</h3>
    <ul>{% for dinner in recommendations.dinners %}<li>{{ dinner }}</li>{% endfor %}</ul>

    <h3>Additional Tips</h3>
    <ul>{% for tip in recommendations.additional_tips %}<li>{{ tip }}</li>{% endfor %}</ul>
</div>
{% endif %}
</body>
</html>

