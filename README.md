# ReplyByMail

Reply by mail为您提供了最简单和易用的API接口，只需要两个API接口即可实现。分别是发送和接收邮件的API，通过Rbm的发送接口发送的邮件，当该邮件被回复时，rbm会将邮件内容通知您的HTTP API，实现通过邮件回复您应用内的消息。

## POST /mail

发送邮件接口，除了普通邮件需要的数据以外，还需要提供一个id参数，当该邮件被回复时，id同时发送。

例:在一个论坛应用里可以用主题的ID作为上下文ID，当用户回复邮件时，邮件内容作为帖子的回复。

## 请求参数

### enctype
- multipart/form-data
- application/x-www-form-urlencoded

Name |  Type  | Required | Description
-----|--------|----------|-------------
accessKey|String|Yes|nySsGjM4FE3bqwxvAeGLHd2hOrTnKxip8oYqcewt
secretKey|String|Yes|nySsGjM4FE3bqwxvAeGLHd2hOrTnKxip8oYqcewt
to|Email|Yes|一个或者多个邮件地址，用,号分割：founder@replybymail.com,mail@replybymail.com
subject|String|Yes|电子邮件的主题
text|String|Yes|电子邮件的Text
html|String|Yes|电子邮件的HTML
id|String|Yes|用于跟踪这封邮件的ID，当你接收到邮件到达的通知请求时，这个ID将会包含在请求的数据里面

## POST /mail/in/webhook

接收邮件通知的接口，这个接口运行在你的HTTP服务器上，当邮件到达时ReplyByMail将会发送POST方法的HTTP请求到这个API。

接收通知的URL地址在控制台内自定义。

## 接受参数

### enctype
- multipart/form-data
- application/x-www-form-urlencoded

Name |  Type  | Required | Description
-----|--------|----------|-------------
access_key|String|Yes|nySsGjM4FE3bqwxvAeGLHd2hOrTnKxip8oYqcewt
secret_key|String|Yes|nySsGjM4FE3bqwxvAeGLHd2hOrTnKxip8oYqcewt
from|Email|Yes|一个或者多个邮件地址，用,号分割：founder@replybymail.com,mail@replybymail.com
cc|Email|Yes|一个或者多个邮件地址，用,号分割：founder@replybymail.com,mail@replybymail.com
subject|String|Yes|电子邮件的主题
text|String|Yes|电子邮件的Text
html|String|Yes|电子邮件的HTML
id|String|Yes|用于跟踪这封邮件的ID，当你接收到邮件到达的通知请求时，这个ID将会包含在请求的数据里面
received_at|Date|Yes|接收到邮件的时间

## 响应
