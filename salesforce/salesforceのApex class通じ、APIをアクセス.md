- 先ず「指定ログイン情報」を作成、
![スクリーンショット 2022-07-26 22.42.19.png](https://raw.githubusercontent.com/PluckYang/Development-Note/main/picture/68747470733a2f2f71696974612d696d6167652d73746f72652e73332e61702d6e6f727468656173742d312e616d617a6f6e6177732e636f6d2f302f323734373338342f33633961393266622d653162372d336437662d336364612d3734333464643361366138382e706e67.png)
- 次Apex classの中request作成、send()メソッドでresponseを貰う、
    ```
    Http http = new Http();
    HttpRequest request = new HttpRequest();
    request.setTimeout(120000);

    //setEndpoint()で「指定ログイン情報」/「アクセスパス」の形で設置
    //以下の例では、「RMS_APIGW」と言う指定ログイン情報のapiをアクセス、apiの具体のパスは：「/devices/cameras/standard_img/approval」
    request.setEndpoint(
      'callout:RMS_APIGW/api/devices/cameras/standard_img/approval'
    );

    request.setMethod('POST');
    request.setHeader('Authorization', IdToken);
    //受信可能なレスポンスデータのメディアタイプを指定
    request.setHeader('Accept', 'application/json');
      
    response = http.send(request);
    System.debug('★' + 'response : ' + response);

    return response;
    ```
- apiの設定により、requestにbodyが必要と必要無い場合がある、
  - 必要の場合（大体json形式）
    ```
    String json =
      '{' +
        '"項目名１" : "' + 値１ + '",' +
        '"項目名２" : "' + 値２ + '",' +
        '"項目名３" : "' + 値３ + '",' +
        '"サブjson" : {' +
          '"サブ項目名１" : "' + サブ値１ + '",' +
          '"サブ項目名２" : "' + サブ値２ + '"' +
       '}' +
     '}';
     request.setBody(json);
     ```
  - 必要無い場合（大体pathで情報含む）
    例えば：apiの具体のパスは：「/devices/cameras/[項目]/standard_img/approval」の場合、request.setEndpoint()には以下のように設定：
    ```
    request.setEndpoint(
      'callout:RMS_APIGW/api/devices/cameras/' + 
      [項目] + 
      '/standard_img/approval'
    );
    ```
参考：[コールアウトエンドポイントとしての指定ログイン情報](https://developer.salesforce.com/docs/atlas.ja-jp.apexcode.meta/apexcode/apex_callouts_named_credentials.htm)
