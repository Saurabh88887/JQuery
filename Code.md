<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <title>Enhanced jQuery Demo Showcase</title>
    
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    
    <style>
        body {
            font-family: 'Arial', sans-serif;
            background-color: #f4f4f4;
            margin: 0;
            padding: 20px;
        }

        h1 {
            text-align: center;
            margin-bottom: 20px;
            color: #333;
        }

        .section {
            background: white;
            padding: 20px;
            margin-bottom: 20px;
            border-radius: 10px;
            box-shadow: 0 0 10px rgba(0,0,0,0.1);
            transition: box-shadow 0.3s ease-in-out;
        }

        .section:hover {
            box-shadow: 0 0 15px rgba(0,0,0,0.2);
        }

        h3 {
            color: #444;
            margin-bottom: 10px;
        }

        button, input[type="submit"] {
            padding: 10px 20px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            margin-top: 10px;
            transition: background-color 0.3s ease-in-out;
        }

        button:hover, input[type="submit"]:hover {
            background-color: #218838;
        }

        ul {
            list-style-type: none;
            padding-left: 0;
        }

        ul li {
            background: #007bff;
            color: white;
            margin: 5px 0;
            padding: 10px;
            border-radius: 5px;
        }

        #box, #slide-box {
            margin-top: 10px;
            background: red;
            width: 100px;
            height: 100px;
            border-radius: 5px;
            transition: background-color 0.3s ease-in-out;
        }

        #slide-box {
            background: blue;
        }

        #fade-button, #toggle-slide {
            display: inline-block;
        }

        #hover-result, #form-result {
            margin-top: 10px;
            font-weight: bold;
            color: #555;
        }

        #data-result {
            margin-top: 10px;
            background: #f0f0f0;
            padding: 10px;
            border-radius: 5px;
            border: 1px solid #ddd;
        }

        #form-validation input[type="text"] {
            padding: 10px;
            margin-right: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
    </style>
</head>
<body>
    <!-- 1. DOM Manipulation -->
    <div id="dom-manipulation" class="section">
        <h3>DOM Manipulation</h3>
        <button id="add-item">Add Item</button>
        <button id="remove-item">Remove Item</button>
        <ul id="item-list">
            <li>Item 1</li>
        </ul>
    </div>

    <!-- 2. Event Handling -->
    <div id="event-handling" class="section">
        <h3>Event Handling</h3>
        <button id="hover-button">Hover over me</button>
        <p id="hover-result">Nothing happened yet.</p>
    </div>

    <!-- 3. Animations -->
    <div id="animations" class="section">
        <h3>Animations</h3>
        <button id="fade-button">Fade Out</button>
        <div id="box"></div>
    </div>

    <!-- 4. AJAX Requests -->
    <div id="ajax" class="section">
        <h3>AJAX Example</h3>
        <button id="load-data">Load Data</button>
        <div id="data-result">AJAX data will appear here</div>
    </div>

    <!-- 5. Form Validation -->
    <div id="form-validation" class="section">
        <h3>Form Validation</h3>
        <form id="my-form">
            <input type="text" id="name" placeholder="Enter your name"/>
            <input type="submit" value="Submit"/>
            <p id="form-result"></p>
        </form>
    </div>

    <!-- 6. Effects (hide, show, slide, etc.) -->
    <div id="effects" class="section">
        <h3>Effects</h3>
        <button id="toggle-slide">Slide Toggle</button>
        <div id="slide-box"></div>
    </div>

    <!-- 7. DOM Traversal -->
    <div id="dom-traversal" class="section">
        <h3>DOM Traversal</h3>
        <ul id="traversal-list">
            <li>Item 1</li>
            <li>Item 2</li>
            <li>Item 3</li>
        </ul>
        <button id="highlight-sibling">Highlight Next Sibling</button>
    </div>

    <script>
        $(document).ready(function(){
            // 1. DOM Manipulation
            $('#add-item').click(function(){
                $('#item-list').append('<li>New Item</li>').hide().fadeIn(500);
            });

            $('#remove-item').click(function(){
                $('#item-list li:last-child').fadeOut(500, function() {
                    $(this).remove();
                });
            });

            // 2. Event Handling
            $('#hover-button').hover(
                function() {
                    $('#hover-result').text('You are hovering!');
                    $(this).css('background-color', '#ffc107');
                },
                function() {
                    $('#hover-result').text('Nothing happened yet.');
                    $(this).css('background-color', '#28a745');
                }
            );

            // 3. Animations
            $('#fade-button').click(function(){
                $('#box').fadeOut(1000, function() {
                    $(this).css('background-color', '#6c757d').fadeIn(500);
                });
            });

            // 4. AJAX Requests
            $('#load-data').click(function(){
                $('#data-result').text('Loading data...');
                $.ajax({
                    url: 'https://jsonplaceholder.typicode.com/posts/1',
                    type: 'GET',
                    success: function(result){
                        $('#data-result').html('<p><strong>Title:</strong> ' + result.title + '</p><p><strong>Body:</strong> ' + result.body + '</p>');
                    }
                });
            });

            // 5. Form Validation
            $('#my-form').submit(function(e){
                e.preventDefault();
                var name = $('#name').val();
                if(name === ""){
                    $('#form-result').text('Please enter your name').css('color', 'red');
                } else {
                    $('#form-result').text('Hello, ' + name + '!').css('color', 'green');
                }
            });

            // 6. Effects (hide, show, slide, etc.)
            $('#toggle-slide').click(function(){
                $('#slide-box').slideToggle(700);
            });

            // 7. DOM Traversal
            $('#highlight-sibling').click(function(){
                $('#traversal-list li:first').next().css('background-color', '#ffc107');
            });
        });
    </script>
</body>
</html>
