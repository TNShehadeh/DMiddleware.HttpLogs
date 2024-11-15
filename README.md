<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
 
</head>
<body>

<h1>Request Logging Middleware</h1>

<p>The <strong>Request Logging Middleware</strong> is a custom ASP.NET Core middleware designed to log detailed information about incoming HTTP requests and their corresponding responses. It provides functionality to capture various metrics, including CPU and memory usage, response times, and request details, enhancing monitoring and troubleshooting capabilities in your application.</p>

<h2>Key Features</h2>
<ul>
    <li><strong>Request and Response Logging</strong>: Logs the HTTP method, path, timestamp, and response status, along with request and response bodies (configurable).</li>
    <li><strong>Performance Metrics</strong>: Tracks CPU usage, memory consumption, and request duration for each processed request.</li>
    <li><strong>Error Handling</strong>: Captures and logs detailed error information if exceptions occur during request processing.</li>
    <li><strong>Configurable Options</strong>: Easily configurable options to choose what data to log (request body, headers, response, etc.).</li>
    <li><strong>Database Integration</strong>: Utilizes a database context to persist log entries for further analysis.</li>
</ul>

<h2>Usage</h2>
 <h3>appSettings.json</h3>
    <p>insert the following configuration into <code>appSettings.json</code> file:</p>
    <pre><code>{
    "HTTPLogConnection": {
        "DatabaseProvider": "", // SQL or PostgreSQL, the default is SQL
        "DefaultConnection": ""
    }
}</code></pre>


<p>To use this middleware, configure it in your ASP.NET Core application’s startup/program.cs:</p>

<pre><code>services.ConfigureDMiddlewareServices(options =&gt;
{
    options.SaveRequestBody = true;
   options.SaveRequesterInfo = true;
   options.SaveRequestHeader = true;
   options.SaveResponse = true;
   options.LogTheLoggDashboard = false;
});</code></pre>

<p>Then add the middleware to the request pipeline:</p>

<pre><code>app.UseRequestLogging();</code></pre>

<h4>Accessing the Logs Dashboard</h4>

<p> To access the logs dashboard, you can map the dashboard route by adding the following to your Configure method in Startup.cs or Program.cs:</p>

<pre><code>app.MapDLoggerDashboard();</code></pre>
<p>Once the dashboard is configured, you can access it via the following URL:</p>
<pre><code>yourURL/DLogger/index.html</code></pre>

<p>This middleware helps developers monitor application behavior and diagnose issues effectively, making it an essential tool for robust application logging.</p>



</body>
</html>
