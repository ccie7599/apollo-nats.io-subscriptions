# Apollo Server for subscriptions via nats.io 

Simple Apollo server that connects to a local nats.io node, and sends messages received on the "MESSAGE_ADDED" nats subject to a messageAdded Apollo subscription.

* Server endpoints are ```https://localhost:4000/graphql``` and ```wss://localhost:4000/graphql```
* The server requires a fullchain.pem and privkey.pem key/cert pair to enable TLS connections.
* A heartbeat NATS publish to the subscription is included in the server, as well as Apollo Hello World query.

To test: 

1. Ensure a nats.io server is running locally, or change the code to point to your specific NATS instance/authentication.
2. Ensure the cert keypairs are present.
3. install dependencies via ```npm install```
4. run the server via ```node server.js```
5. Go to https://{server}:4000/graphql and navigate to Apollo Studio via link.
6. Run the following operation and the heartbeat subscription message stream should appear in the console.
```
subscription {
  messageAdded
}
```
![image](https://github.com/user-attachments/assets/2892f2d5-da0b-4289-8518-51243bb9eda7)
