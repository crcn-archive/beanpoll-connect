### Example

```javascript
var express     = require("express"),
beanpoll        = require("beanpoll"),
beanpollConnect = require("beanpoll-connect"); 


var router = beanpoll.router();

router.on({
	"pull auth": function(req, res) {
		if(req.query.user == "user" && req.query.pass == "pass") {
			this.next();
		}
	},
	"pull -method=GET auth -> saveProfile": function(req, res) {
		res.end("success!");
	}
});


var server = express();
server.use(beanpollConnect.middleware(router));

server.listen(8080); //access saveProfile from the web

```