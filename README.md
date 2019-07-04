# How to run

	* set up npm and node js [https://www.npmjs.com/get-npm]
	* set up serverless FW [`$ npm install -g serverless`]
	* install npm modules bases on package json [`$ npm install`]
	* install local dynamo db using serverless FW [`$ sls dynamodb install`]
	* run application on local [`$ sls offline start --migrate`]   [3000 port for server and 8000 port for dynamo db]

# References

	* [serverless FW] https://keyholesoftware.com/2018/11/05/building-a-node-js-service-with-aws-lambda-dynamodb-and-serverless-framework/
	* [YAML] https://www.youtube.com/watch?v=cdLNKUoMc6c

# check dynamo db table using aws cli [http://localhost:8000/shell/]
```
aws dynamodb create-table     --table-name  todos-dev    --attribute-definitions         AttributeName=todoId,AttributeType=S     --key-schema AttributeName=todoId,KeyType=HASH     --provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5     --endpoint-url http://0.0.0.0:8000
```

```
aws dynamodb scan --table-name todos-dev --endpoint-url http://0.0.0.0:8000
```

# Curl requests

* List todos
```
curl -H "Content-Type: application/json" -X GET http://localhost:3000/todos/
```

* Insert todo
```
curl -H "Content-Type: application/json" -X PUT http://localhost:3000/todos -d '{"todoId": "5c30e169-26e3-44de-9564-d23a403ddf1b", "title": "Finish bug tickets", "done": "false"}'
```

* Delete todo
```
curl -H "Content-Type: application/json" -X DELETE http://localhost:3000/todos/5c30e169-26e3-44de-9564-d23a403ddf1b
```

# React template
* https://www.reactboilerplate.com/
