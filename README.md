# TestTeamWork
// server.js
const jsonServer = require('json-server')
const server = jsonServer.create()
const router = jsonServer.router('db.json')
const middlewares = jsonServer.defaults()

server.use(middlewares)
server.use(router)
server.listen(3000, () => {
  console.log('JSON Server is running')
})

![SinhVien](https://github.com/Tien-Tiny/TestTeamWork/assets/89054978/a14d9482-5952-4291-a06c-174f28766e6b)


