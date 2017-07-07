
Releasing clldutils
===================

Clone clld/clldutils and switch to the master branch. Then:

- Do platform test via tox (making sure statement coverage is at 100%):
```
tox -r
```

- Make sure flake8 passes::
```
flake8 --ignore=E711,E712,D100,D101,D103,D102,D301 --max-line-length=100 clldutils
```

- Change version to the new version number in

  - setup.py
  - clldutils/__init__.py

- Bump version number:
```
git commit -a -m"bumped version number"
```

- Create a release tag:
```
git tag -a v<version> -m"first version to be released on pypi"
```

- Push to github:
```
git push origin
git push --tags
```

- Make sure your system Python has ``setuptools-git`` installed and release to
  PyPI:
```
git checkout tags/v$1
python setup.py sdist
~/venvs/py34/bin/twine upload dist/clldutils-<version>.tar.gz
```
