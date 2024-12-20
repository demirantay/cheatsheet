# Deployment Checklist

### Rules

> FOR NOW DO THIS MANUALLY IN NEXT ITERATIONS MAKE IT AUTOMATED

- Production Code will never push code to github
- It will always pull from github

### Dev (local) To-Do

- [ ] Finish everything on trello
- [ ] Polish the last details on app's modules
- [ ] Don't forget to check config/dev_settings.py

### Git Server To-Do

- [ ] Merge master with new branch
- [ ] Update git tags
- [ ] upload new git tag
- [ ] make sure everything works perfectly on git master branch

### Production To-Do

- [ ] After ssh check if everything works correctly, check the site manually
      (check if posgres server, nginx running in the background)
- [ ] BACKUP
- [ ] Check if env_vars are working (manually check the site it will tell you)
- [ ] Check if secret key is read from a file & the db password
- [ ] Git pull the codes
- [ ] check new pip packages to be downloaded from requirements.txt
- [ ] Compare dev_settings -- settings.py
- [ ] Update settings.py's lacking new features from dev_settings
- [ ] Add a a env var DB_USER_PASSWORD -- > e********d
- [ ] with main settings.py makemigrations
- [ ] with main settings.py migrate
- [ ] with main settings.py collectstatic
- [ ] Run manage.py check --deploy
- [ ] Stop gunicorn process that is currenly running in background
- [ ] restart application server gunicorn with main settings.py
      (this time I had to run it in the background with this: nohup ./gunicorn_start.sh &)
- [ ] reload nginx
