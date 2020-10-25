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




<br />
<br />


 _____________________________________________________
 _____________________________________________________


<br />
<br />

# Message

## Send Message from Client to Server
```javascript
// ## SERVER SIDE ##
socket.on('chat message', (msg) => {
   console.log('message: ' + msg);
});

// ## CLIENT SIDE ##
socket.emit('chat message', $('#m').val());
```


<br />
<br />


 _____________________________________________________
 _____________________________________________________


<br />
<br />

# Room


## Connect to Room
```javascript
// ## SERVER SIDE ##
socket.on('chat connect', (msg) => {
console.log('connect - message: ' + JSON.stringify(msg, null, 4));

        socket.join(msg.room);

});

// ## CLIENT SIDE ##
socket.emit('chat connect', {"room": details.room, "usertoken": details.usertoken}); // <-- user token is optional here.. but maybe usefully for future production..
```





<br />
<br />



## Send Message to Room
```javascript
// ## SERVER SIDE ##
socket.on('chat message', (msg) => {
console.log('chat message - message: ' + JSON.stringify(msg, null, 4));

        socket.to(msg.room).emit('msg', msg.msg);

});

// ## CLIENT SIDE ##
socket.emit('chat message', {"msg": msg, "room": details.room, "usertoken": details.usertoken}); // <-- user token is optional here.. but maybe usefully for future production..
```


