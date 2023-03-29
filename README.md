# compute-version

Remote develop branch:

```
docker run --rm -v $(pwd):/repo gittools/gitversion:6.0.0-beta.1 \
    /repo \
    /url https://github.com/xpicio/compute-version.git \
    /b develop
```

Remote main branch:

```
docker run --rm -v $(pwd):/repo gittools/gitversion:6.0.0-beta.1 \
    /repo \
    /url https://github.com/xpicio/compute-version.git \
    /b main
```

Local branch:

```
docker run --rm -v $(pwd):/repo gittools/gitversion:6.0.0-beta.1 /repo
```
