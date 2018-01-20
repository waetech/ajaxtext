# ajaxtext
This project is about loading a simple text file using AJAX and Javascript into a simple web page.
<<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Ajax 1 - Text File</title>

</head>
<body>
    <button id="button">Get Text File</button>
    <br><br>
    <div id="text"></div>

    <script>
    //Create event listener
    document.getElementById('button').addEventListener('click', loadText);

    function loadText(){
        //Create XHR object
        var xhr = new XMLHttpRequest();
        //Open - type, url/file, async
        xhr.open('GET', 'sample.txt', true);

        //Optional - used for loaders
        xhr.onprogress = function(){
            //console.log('READYSTATE: ', xhr.readyState);
           
        }

        xhr.onload = function(){
            if(this.status === 200){
                //console.log(this.responseText);
                document.getElementById('text').innerHTML = this.responseText;
            }else if(this.status == 404){
                 document.getElementById('text').innerHTML = 'Error 404 Not found';
            }else if(this.status === 403){
                document.getElementById('text').innerHTML = 'Error 403 Forbidden';
            }else if(this.status === 500){
                document.getElementById('text').innerHTML = 'Error 500 Internal Server Error';
            }

        }

        xhr.onerror = function(){
            console.log('Request error...');
        }
        //Sends request
        xhr.send();
    }
    </script>
</body>
</html>
