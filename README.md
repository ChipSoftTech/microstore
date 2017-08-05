# microstore
A micro application used to store data.  File based RESTful API.  Useful for microservices or client side applications that need a simple data store.  

## Run
npm install
npm run-script build
node ./lib/server.js

## Usage
Data is stored in JSON files, one file per api route. For example, all requests to `/api/users` will read and update from users.json.

### Usage example
1. Start server, storing files in the `json` directory: `microstore --data json`.
2. Add a record from the command line: `curl http://localhost:3000/api/contacts -H "Content-Type: application/json" -d '{ "name": "Brian Carter", "email": "briancarter@chipsofttech.com" }' -X POST`
3. Query all records from the command line: `curl http://localhost:3000/api/contacts`

### REST API
- `GET /api/route`: Returns all elements in the JSON file specified by the route.
- `POST /api/route`: Adds an element at the end of the JSON file specified by the route. If not present, adds an `_id` property with a unique value, useful for GET/PUT/Delete operations.
- `PUT /api/route/id`: Updates the element identified by `id`.
- `DELETE /api/route/id`: Removes the element identified by `id`.
- `GET /api/route/id`: Returns a single element identified by `id`.

### Command-line parameters
- `--port`: HTTP port to be used. Defaults to 3000.
- `--data`: directory used to store JSON files. Defaults to working directory.
- `--prefix`: API prefix. Defaults to /api.
- `--static`: directory used for static content. Disabled by default.
- `--delay`: response delay in milliseconds. Defaults to 0.
- `--write-time`: interval between file updates in milliseconds. Defaults to 100. If set to 0, data will not be written to file.
- `--disable-cors`: enable/disable CORS. It is enabled by default, so that requests can be sent from pages served from any host or port.
