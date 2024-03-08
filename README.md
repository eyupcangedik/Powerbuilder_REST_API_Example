// Content-Type = application/json

integer li_rc
string ls_Request, ls_Url, ls_Response


HttpClient lnv_HttpClient
lnv_HttpClient = Create HttpClient

ls_Url = "http://localhost/UserService/api/InsertUser"

lnv_HttpClient.SetRequestHeader("Content-Type", "application/json")
lnv_HttpClient.SetRequestHeader("username", "user1234")
lnv_HttpClient.SetRequestHeader("password", "pass1234")

ls_Request = '{"ID":"1905","Name":"Eyüp Can","Surname":"Gedik","Status":"A","DateOfBirth":"1999-09-13"}'
li_rc = lnv_HttpClient.SendRequest('POST', ls_url, ls_Request)

if li_rc = 1 and lnv_HttpClient.GetResponseStatusCode() = 200 then
 lnv_HttpClient.GetResponseBody(ls_Response)
end if

--------------------------------------------------------------------------------------------------------

//Content-Type = application/x-www-form-urlencoded

integer li_rc
string ls_Request, ls_Url, ls_Response
string ls_state, ls_grant_type, ls_scope, ls_username, ls_password, ls_client_id, ls_client_secret

HttpClient lnv_HttpClient
lnv_HttpClient = Create HttpClient

ls_Url = "https://localhost/auth/oauth/v2/token"
lnv_HttpClient.SetRequestHeader("Content-Type", "application/x-www-form-urlencoded")

ls_state = "state=init&"
ls_grant_type = "grant_type=password&"
ls_scope = "scope=user-service&"
ls_username = "username=user1234&"
ls_password = "password=pass1234&"
ls_client_id = "client_id=0245e6r5-95f0-4ec6-74z6-84f76a85c8s1&"
ls_client_secret = "client_secret=kf7c46dd-40b7-2194-8b79-68d59wr5c040&"

ls_Request = ls_state + ls_grant_type + ls_scope + ls_username + ls_password + ls_client_id + ls_client_secret

li_rc = lnv_HttpClient.SendRequest('POST', ls_Url, ls_Request)

if li_rc = 1  then
 lnv_HttpClient.GetResponseBody(ls_Response)
end if

--------------------------------------------------------------------------------------------------------

