#web 

# pre-request script
> 是可以在 request 執行之前執行的 js code。會有一些 postman 提光的 api 可以串接。

[參考資料](https://blog.dtask.idv.tw/Postman/Postman_PreRequestScript_Token_API/)

範例 code: 
```js
const base_url = pm.environment.get("base_url");

pm.sendRequest({
	url: `${base_url}/mgmt/login`,
	method: 'POST',
	body: {
		mode: 'raw',
		raw: JSON.stringify({
		username: "inncom",
		password: "cloud"
		})
	}
}, function(err, response) {
	const jsonResponse = response.json();
	pm.environment.set("mgmt_jwt", jsonResponse.jwt);
});
```
> pm 就是 postman 所提供的 api。