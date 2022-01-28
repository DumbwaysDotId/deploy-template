# Deploy frontend to netlify

`Netlify` is a San Francisco-based cloud computing company that offers hosting and serverless backend or frontend services for web applications and static websites.

- First create repository & push frontend project

- Go to [Netlify](http://netlify.com) → Login → Click `New site from Git`

* Connect to Git provider, click `Github`

* Pick a repository

* Site settings, and deploy

* Scroll down, modify Build command to `CI= npm run build`. Click `Show advanced`

* Click `New variable` for add `environment variables`.  Like: `REACT_APP_SERVER_URL`

* Click `Deploy site`

* Wait deploy progress

* Click the link for open web
