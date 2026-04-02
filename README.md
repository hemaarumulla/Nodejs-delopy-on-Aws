
**STEP 1: ADD REQUIRED REPO FROM OFFICIAL NODEJS WEBSITE.**

```bash
curl -sL https://rpm.nodesource.com/setup_14.x | sudo bash -
```

**STEP 2: INSTALL NODEJS.**

```bash
sudo yum install -y nodejs
```

**STEP 3: VERIFY INSTALLED VERSION.**

```bash
node -v
npm -v
```

**STEP 4: CREATE A server.js FILE AND RUN IT.**

Create a file named `server.js` with the provided the below content.

```bash
const http = require('http');
const fs = require('fs');
const path = require('path');

const server = http.createServer((req, res) => {
  const filePath = path.join(__dirname, 'index.html');
  const stat = fs.statSync(filePath);

  res.writeHead(200, {
    'Content-Type': 'text/html',
    'Content-Length': stat.size,
  });

  const readStream = fs.createReadStream(filePath);
  readStream.pipe(res);
});

const PORT = 80;
server.listen(PORT, () => {
  console.log(`Server is running on http://localhost:${PORT}`);
});

```

this script creates a basic web server that listens on port 80, reads the content of an `index.html` file, and sends it as the response when a request is made to the server. The server logs a message indicating that it is running on `http://localhost:80`.

**STEP 5: INSTALL REQUIRED PACKAGES / INSTALL DEPENDENCIES.**

```bash
npm install
```

**STEP 6: NODE.JS WILL INTERPRET AND EXECUTE THE CODE IN THE server.js FILE. THIS IS A COMMON PATTERN FOR RUNNING SERVER-SIDE JAVASCRIPT APPLICATIONS.**

```bash
node server.js
```

**After following these steps, your Node.js server should be up and running.**

**Make sure your ec2 instance security group io opened with required port i.e; 80/3000/any toher port**

========================================================================================================================

**PM2 useful Commands**

**Command to install pm2**

```bash
npm install -g pm2
```

**list all running processes/apps.**

```bash
pm2 list   (or) pm ls
```

**Start app/services with name**

```bash
pm2 start server.js --name "my-app1"
```

**Command to list the logs**

```bash
pm2 logs id/name
```

ex: pm2

**Command to Monitor the resources**

```bash
pm2 monit
```

**To make service as startup**

```bash
pm2 startup
```

**Command to delete service/app**

```bash
pm2 delete name/id
```
**reload after any  changes
```bash
pm2 reload 0
```

```bash
pm2 list
```
**to show all info
```bash
pm2 show 0
```

