
-- functions 
-- F_CLIENTS_PASSWORD_CHECK
SET @p0='test'; 
SET @p1='test'; 
SET @p2='test'; 
SELECT `F_CLIENTS_PASSWORD_CHECK`(@p0, @p1, @p2) AS `F_CLIENTS_PASSWORD_CHECK`;

this function returns -1,0,1 values

if user not found returns -1

if found or password not match returns 0 or 1

if password matched then updates  "KRN_CLIENTS" table to "CLIENT_ATTEMPTS" to 0
if password not matched, updates "KRN_CLIENTS" tale to "CLIENT_ATTEMPTS" increases +1

after checking password, inserts data to KRN_CLIENT_VERIFY_HIST table 





--function
-- F_CLIENT_NEW_TOKEN

SET @p0='2'; 
SELECT `F_CLIENT_NEW_TOKEN`(@p0) AS `F_CLIENT_NEW_TOKEN`;

this function returns TOKEN string or empty string

if user found then generates net token and inserts into "KRN_CLIENT_TOKEN" table and returns TOKEN
if user not found returns empty string;




--TRIGGERS

--trigger_krn_clients_passowrd_hash
befoure inserting new client updates insert password to hashed password

--trigger_krn_client_token_generate
...