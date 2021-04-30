Setting up Github CLI
Setting up GitHub auth with HTTPS

You can set up Github auth via HTTPS by setting up a Personal Access Token(PAT).

Steps to create a PAT with your account

  1. Navigate to your Github account homepage

  2. Verify your email address, if it hasn't been verified yet.

  3. In the upper right corner of your page, click your profile photo, and then click settings

  4. In the Settings tab, on the left sidebar, click Developer settings

  5. In the left sidebar, click Personal access tokens.

  6. Click Generate new token.

  7. Give a descriptive name to your token

  8. Select the scopes, or permissions, you'd like to grant this token. To use your token to access repositories from the command line, select repo.

  9. Click Generate token.

  10. Copy the PAT in your clipboard. Github has imposed a security measure as once we navigate off the page we might not be able to see the token generated . 
  
  11. It is advised to save the token somewhere else. You should treat your tokens like password.

Once the token is set up, you could use this token as a password when performing Git operations over HTTPS. 

For instance, if you want to clone a private repository, if your PAT has granted access repositories from the command line, you could use it directly as your password.

```
$ git clone https://github.com/username/repo.git
Username: your_username
Password: your_token
```
 
