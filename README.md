# comp2068-lab2
var http = require('http');

// require node's url module to parse the url's querystring
var url = require('url');

// create the server to run the page
http.createServer(function(req,res)
{

    // get the querystring and parse x and y as a float value
    var qs = url.parse(req.url, true).query;

    var method = qs.method;
    var x = parseFloat(qs.x);
    var y = parseFloat(qs.y);

    //Calculate in 4 cases, method are: "add", "subtract", "multiply", and "divide"
     function output(x, y, method)
    {
        if (method == "add")
            {
                return x + y;
            }
        else if (method == "subtract")
            {
                return x - y;
            }
        else if (method == "multiply")
            {
                return x * y;
            }
        else if (method == "divide")
            {
                return x / y;
            }     
     }

    // output all the values
    res.write('<h1>x:</h1>' + x + '<br />' + '<h1>y:</h1>' + y + '<br />' + '<h1>method:</h1>' + method + '<br />' + '<h1>output:</h1>' + output(x,y,method));
    res.end();


}).listen(3000);
// page runs at http://localhost:3000/lab2.js?method=divide&x=&y=
