# Socket.io Cheat Sheet
Cheat Sheet for Socket.io with the most needed stuff..



<br />
<br />


 _____________________________________________________
 _____________________________________________________


<br />
<br />

# Connection
```javascript
// ## SERVER SIDE ##
const http = require('http').createServer(app),
        io = require('socket.io')(http);
io.on('connection', (socket) => {
console.log('User connected..');


   socket.on('disconnect', () => {
          console.log('User disconnected');
   });


});


http.listen(port, () => {
     console.log('Server was started.. Listening on port: ' + port);
});
```

```html
<!-- ## CLIENT SIDE ## -->
<!DOCTYPE html>
<html lang="en">

<head>
<meta
name="description"
content="Example Chat with Socket.io"/>
<title>Example Chat with Socket.io</title>
</head>

  <body>
    <script src="js/socket.io.min.js" defer></script>
    <script>
    const socket = io();
    </script>

  </body>
</html>
```
