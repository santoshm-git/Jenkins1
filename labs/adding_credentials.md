**Add Credentials for GITHUB as User ID & PWD**
1. Got to Jenkins dashboard http://http://3.15.199.147:8080/
2. Select Manage Jenkins
3. Select Manage Credentials
4. Select Store as Jenkins & System as Global
5. Click Add Credentials
6. Select Kind as Username with password, Scope Global
7. Add Username as your GITHUB User, Password as your GITHUB Password & ID & Description as GITHUB-CREDS

### Add private key with user as creadentials
1. Got to Jenkins dashboard http://http://3.15.199.147:8080/
2. Select Manage Jenkins
3. Select Manage Credentials
4. Select Store as Jenkins & System as Global
5. Click Add Credentials
6. Select Kind as SSH Username with private key & Scope as Global
7. Add ID & Description as linux-server-private-key
8. Add Username as the one for which private key to be used, like ubuntu
9. Under private key select Enter directly and click on ADD
10. Insert private-key copied in desired section & click OK.
