# README

## 0. How to use this docker compose

### 0.1 How to start this container

```bash
docker compose up --build --detach -d
# or
npm run docker:up
```

and connect to:

- <http://localhost:9325/>

### 0.2 How to stop and delete container

```bash
docker compose down --volumes --remove-orphans
# or
npm run docker:down
```

## 1. How to create a queue in the AWS

Login "AWS Management Console"
Go to "Amazon SQS"
Click the button "Create queue"

### 1.1 Create Queue

Type in the box {my-queue-name} in the section "Details"
Click the button "Create queue"

#### In the queue created

Copy URL to use to client apps in the section "Details"

### 1.2 Create a client app using JavaScript

#### Create an node project

```bash
mkdir my-client-app
cd my-client-app
npm init -y
npm install --save @aws-sdk/client-sqs
touch credentials.js
touch index.js
```

##### Update `package.json` file to use ES6

`package.json`

```json
{
  "type": "module",
   ...
}
```

#### Case 1. Provide `endpoint` in the `credentials.js`

##### Fill in `credentials.js` with yours

`credentials.js`

```javascript
export const configForAWS = {
 region: "ap-northeast-2",
 credentials: {
  accessKeyId: "MY-ACCESS-KEY-ID",
  secretAccessKey: "MY-SECRET-ACCESS-KEY",
 },
 endpoint: "https://sqs.ap-northeast-2.amazonaws.com/1234567890/my-queue-name",
};
```

##### Implement `index.js` file

`index.js`

```javascript
import {
  SQSClient,
  SendMessageCommand,
  DeleteMessageCommand,
  ReceiveMessageCommand,
} from "@aws-sdk/client-sqs";
import { configForAWS } from "./credentials.js";

const sqsClient = new SQSClient(configForAWS);

const sendMessageToQueue = async (body) => {
  try {
    const command = new SendMessageCommand({
      MessageBody: body,
      MessageAttributes: {
        UserId: { DataType: "String", StringValue: "user-id-01" },
      },
    });
    const result = await sqsClient.send(command);
    console.log(result);
  } catch (error) {
    console.error(error);
  }
};

const deleteMessage = async (receiptHandle) => {
  try {
    const command = new DeleteMessageCommand({
      ReceiptHandle: receiptHandle,
    });
    const result = await sqsClient.send(command);
    console.log(result);
  } catch (error) {
    console.error(error);
  }
};

const pollMessages = async () => {
  try {
    const command = new ReceiveMessageCommand({
      MaxNumberOfMessages: 10,
      WaitTimeSeconds: 5,
      MessageAttributeNames: ["All"],
    });
    const result = await sqsClient.send(command);
    console.log(result);

    // delete message
    const deleteResult = await deleteMessage(result.Messages[0].ReceiptHandle);
    console.log(deleteMessage);
  } catch (error) {
    console.error(error);
  }
};

await sendMessageToQueue("Hello, World!");
await pollMessages();
```

##### Run  the client app

```bash
cd my-client-app
node index.js
```

##### Check the queue in your AWS SQS

visit your AWS SQS

#### Case 2. Do NOT provide  `endpoint` in the `credentials.js`

##### Fill in `credentials.js` with yours

`credentials.js`

```javascript
export const configForAWS = {
 region: "ap-northeast-2",
 credentials: {
  accessKeyId: "MY-ACCESS-KEY-ID",
  secretAccessKey: "MY-SECRET-ACCESS-KEY",
 },
};
```

##### Implement `index.js` file

`index.js`

```javascript
import {
  SQSClient,
  SendMessageCommand,
  DeleteMessageCommand,
  ReceiveMessageCommand,
} from "@aws-sdk/client-sqs";
import { configForAWS } from "./credentials.js";

const sqsClient = new SQSClient(configForAWS);

// endpoint
const queueUrl = "https://sqs.ap-northeast-2.amazonaws.com/1234567890/my-queue-name";

const sendMessageToQueue = async (quequeUrl, body) => {
  try {
    const command = new SendMessageCommand({
   QueueUrl: queueUrl,
      MessageBody: body,
      MessageAttributes: {
        UserId: { DataType: "String", StringValue: "user-id-01" },
      },
    });
    const result = await sqsClient.send(command);
    console.log(result);
  } catch (error) {
    console.error(error);
  }
};

const deleteMessage = async (queueUrl, receiptHandle) => {
  try {
    const command = new DeleteMessageCommand({
   QueueUrl: queueUrl,
      ReceiptHandle: receiptHandle,
    });
    const result = await sqsClient.send(command);
    console.log(result);
  } catch (error) {
    console.error(error);
  }
};

const pollMessages = async (queueUrl) => {
  try {
    const command = new ReceiveMessageCommand({
   QueueUrl: queueUrl,
      MaxNumberOfMessages: 10,
      WaitTimeSeconds: 5,
      MessageAttributeNames: ["All"],
    });
    const result = await sqsClient.send(command);
    console.log(result);

    // delete message
    const deleteResult = await deleteMessage(queueUrl, result.Messages[0].ReceiptHandle);
    console.log(deleteMessage);
  } catch (error) {
    console.error(error);
  }
};

await sendMessageToQueue(queueUrl, "Hello, World!");
await pollMessages(queueUrl);
```

##### Run  the client app

```bash
cd my-client-app
node index.js
```

##### Check the queue in your AWS SQS

visit your AWS SQS

## 2. How to create a queue on local machine

### 2.1 run SQS on Docker

Before that, you should install Docker engine on your machine.

```bash
docker run --name alpine-sqs -p 9324:9324 -p 9325:9325 -d roribio16/alpine-sqs:latest
docker container ls
```

Check the server status with `http://localhost:9325` on your web browser

### 2.2 Create a client app using JavaScript

#### Create an node project

```bash
mkdir my-client-app
cd my-client-app
npm init -y
npm install --save @aws-sdk/client-sqs
touch credentials.js
touch index.js
```

##### Update `package.json` file to use ES6

`package.json`

```json
{
  "type": "module",
   ...
}
```

#### Case 1. Provide `endpoint` in the `credentials.js`

##### Fill in `credentials.js` with yours

`credentials.js`

```javascript
export const configForLocal = {
 endpoint: "http://localhost:9324/queque/default",
};
```

##### Implement `index.js` file

`index.js`

```javascript
import {
  SQSClient,
  SendMessageCommand,
  DeleteMessageCommand,
  ReceiveMessageCommand,
} from "@aws-sdk/client-sqs";
import { configForLocal } from "./credentials.js";

const sqsClient = new SQSClient(configForLocal);

const sendMessageToQueue = async (body) => {
  try {
    const command = new SendMessageCommand({
      MessageBody: body,
      MessageAttributes: {
        UserId: { DataType: "String", StringValue: "user-id-01" },
      },
    });
    const result = await sqsClient.send(command);
    console.log(result);
  } catch (error) {
    console.error(error);
  }
};

const deleteMessage = async (receiptHandle) => {
  try {
    const command = new DeleteMessageCommand({
      ReceiptHandle: receiptHandle,
    });
    const result = await sqsClient.send(command);
    console.log(result);
  } catch (error) {
    console.error(error);
  }
};

const pollMessages = async () => {
  try {
    const command = new ReceiveMessageCommand({
      MaxNumberOfMessages: 10,
      WaitTimeSeconds: 5,
      MessageAttributeNames: ["All"],
    });
    const result = await sqsClient.send(command);
    console.log(result);

    // delete message
    const deleteResult = await deleteMessage(result.Messages[0].ReceiptHandle);
    console.log(deleteMessage);
  } catch (error) {
    console.error(error);
  }
};

await sendMessageToQueue("Hello, World!");
await pollMessages();
```

##### Run  the client app

```bash
cd my-client-app
node index.js
```

##### Check the queue in your local SQS

visit `http://localhost:9325/` and check the "default" tab.

#### Case 2. Do NOT provide  `endpoint` in the `credentials.js`

##### Fill in `credentials.js` with yours

`credentials.js`

```javascript
export const configForAWS = {
 endpoint: "http://localhost:9324/queque/default",
};
```

##### Implement `index.js` file

`index.js`

```javascript
import {
  SQSClient,
  SendMessageCommand,
  DeleteMessageCommand,
  ReceiveMessageCommand,
} from "@aws-sdk/client-sqs";
import { configForLocal } from "./credentials.js";

const sqsClient = new SQSClient(configForAWS);

// endpoint
const queueUrl = "http://localhost:9324/queque/default";

const sendMessageToQueue = async (quequeUrl, body) => {
  try {
    const command = new SendMessageCommand({
   QueueUrl: queueUrl,
      MessageBody: body,
      MessageAttributes: {
        UserId: { DataType: "String", StringValue: "user-id-01" },
      },
    });
    const result = await sqsClient.send(command);
    console.log(result);
  } catch (error) {
    console.error(error);
  }
};

const deleteMessage = async (queueUrl, receiptHandle) => {
  try {
    const command = new DeleteMessageCommand({
      ReceiptHandle: receiptHandle,
    });
    const result = await sqsClient.send(command);
    console.log(result);
  } catch (error) {
    console.error(error);
  }
};

const pollMessages = async (queueUrl) => {
  try {
    const command = new ReceiveMessageCommand({
   QueueUrl: queueUrl,
      MaxNumberOfMessages: 10,
      WaitTimeSeconds: 5,
      MessageAttributeNames: ["All"],
    });
    const result = await sqsClient.send(command);
    console.log(result);

    // delete message
    const deleteResult = await deleteMessage(queueUrl, result.Messages[0].ReceiptHandle);
    console.log(deleteMessage);
  } catch (error) {
    console.error(error);
  }
};

await sendMessageToQueue(queueUrl, "Hello, World!");
await pollMessages();
```

##### Run  the client app

```bash
cd my-client-app
node index.js
```

##### Check the queue in your local SQS

visit `http://localhost:9325/` and check the "default" tab.

### 3. References

- <https://youtu.be/_20HXT43hFk>
