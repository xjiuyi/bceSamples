# java-ses-setFeedback

## 用途：

设置通知方式。

| 代码 | 通知类型 |
| :-- | :-- |
| 1 | 退信或投诉 |
| 2 | 退信 |
| 3 | 投诉 |

## 使用方法：

* 第一步：在代码中配置AK/SK，以及邮箱地址等信息。
* 第二步：执行`App::main`方法。

## 代码简介：

### 第一步：添加`bce-java-sdk`依赖。

```xml
<dependency>
    <groupId>com.baidubce</groupId>
    <artifactId>bce-java-sdk</artifactId>
    <version>0.10.6</version>
</dependency>
```

### 第二步：配置AK/SK，创建SesClient。

```java
String AK = "";  // AccessKeyId
String SK = "";  // SecretAccessKey

SesClientConfiguration configuration = new SesClientConfiguration();
configuration.setCredentials(new DefaultBceCredentials(AK, SK));
SesClient client = new SesClient(configuration);
```

### 第三步：设置通知方式。

```java
SetFeedbackRequest request = new SetFeedbackRequest();
request.setType(2);  // 通知类型：1 退信或投诉，2 退信，3 投诉
request.setEmail();  // 接收通知的邮箱地址, 比如: xyz@abc.com
request.setEnabled(true);  // true：接收通知，false：不接收通知
client.setFeedback(request);
```