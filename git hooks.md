# Git hooks

[https://www.atlassian.com/git/tutorials/git-hooks](https://www.atlassian.com/git/tutorials/git-hooks)

Git hooks are scripts that run automatically every time a particular event occurs in a git repository,

Common use cases for git hooks include encouraging a commit policy, altering the project environment depending on the sate of the repository, and implementing continous integration workflows, etc..

## Installing hooks

Hooks reside in the .git/hooks directory of every git repository, git automatically populates this directory when you initialize a repository.

The build-in scripts are mostly shell and PERL, if you use another script, all you have to do is change it to the path of your interpreter.

```python

#!/usr/bin/env python

import sys, os

commit_msg_filepath = sys.argv[1]
with open(commit_msg_filepath, 'w') as f:
    f.write('# Please include a useful commit message!')

```

## Hook scope

1. local hooks

   local hooks only affect the repository in which they resids.

   below example is a Post-commit hook:

```python
 #!/usr/bin/env python

import smtplib
from email.mime.text import MIMEText
from subprocess import check_output


log = check_output(['git', 'log', '-1', '--stat', 'HEAD'])


msg = MIMEText("Look, I'm actually doing some work:\n\n%s" % log)

msg['Subject'] = 'Git post-commit hook notification'
msg['From'] = 'mary@example.com'
msg['To'] = 'boss@example.com'


SMTP_SERVER = 'smtp.example.com'
SMTP_PORT = 587
session = smtplib.SMTP(SMTP_SERVER, SMTP_PORT)
session.ehlo()
session.starttls()
session.ehlo()
session.login(msg['From'], 'secretPassword')

session.sendmail(msg['From'], msg['To'], msg.as_string())
session.quit()
```

2. Server side hooks

Server side hooks work just like local ones, except they reside in server side repositories.

there are 3 server side hooks:

* pre-receive
* update
* post-receive