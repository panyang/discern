=================================
Installation Overview
=================================
Looking at fabfile.py is also a good idea of how to install this.  The commands in fabfile will take a system
from a fresh start to a fully working install.
The main steps are:

1. apt-get install git python
2. git clone git@github.com:edx/discern.git
3. xargs -a apt-packages.txt apt-get install
4. apt-get install python-pip
5. pip install virtualenv
6. virtualenv /opt/edx
7. source /opt/edx/bin/activate
8. cd discern
9. pip install -r pre-requirements.txt
10. pip install -r requirements.txt
11. python manage.py syncdb --settings=discern.settings --noinput --pythonpath=DIR WHERE YOU CLONED REPO
12. Choose "no" for create superuser if syncdb prompts you for it.
13. python manage.py migrate --settings=discern.settings --noinput --pythonpath=DIR WHERE YOU CLONED REPO
14. python manage.py collectstatic -c --noinput --settings=discern.settings --pythonpath=DIR WHERE YOU CLONED REPO

See "usage" for how to run this.  You will both need to run the server and the celery tasks.

You can skip the virtualenv commands if you like, but they will be a major help in keeping the packages
for this repo separate from the rest of your system.

If you get errors using the above, you may need to create a database directory one level up from where you cloned
the git repo (folder named "db")

You will need to install the ease repo (https://github.com/edx/ease) in the same base directory that you installed discern in order to get all functionality.  Follow the install instructions in that repo.
