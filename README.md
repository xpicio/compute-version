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

## Compute Behavior

Start from tag v0.2.4 with conventional commits messages.

| action                  | branch   | commit message                         | SemVer           | FullSemVer         |
| ----------------------- | -------- | -------------------------------------- | ---------------- | ------------------ |
| commit                  | develop  | chore: update GitVersion configuration | 0.3.0-alpha.1    |                    |
| commit                  | develop  | fix: update file                       | 0.3.0-alpha.2    |                    |
| commit                  | develop  | fix: update file 2                     | 0.3.0-alpha.3    |                    |
| create new feature      | arch-899 |                                        | 0.3.0-arch-899.1 | 0.3.0-arch-899.1+3 |
| commit                  | arch-899 | fix: update file 3                     | 0.3.0-arch-899.1 | 0.3.0-arch-899.1+4 |
| commit                  | arch-899 | feat: update file 4                    | 0.3.0-arch-899.1 | 0.3.0-arch-899.1+5 |
| close feature           | arch-899 |                                        |                  |                    |
|                         | develop  |                                        | 0.3.0-alpha.6    | 0.3.0-alpha.6      |
| create release          |          |                                        |                  |                    |
| close release           |          |                                        |                  |                    |
|                         | develop  |                                        | 0.3.0-alpha.8    | 0.3.0-alpha.8      |
|                         | main     |                                        | 0.3.0-rc.7       | 0.3.0-rc.7         |
| tag (production deploy) | main     |                                        | 0.3.0-7          | 0.3.0-7            |

Start from tag v0.3.0.

| action             | branch   | commit message                  | SemVer           | FullSemVer         |
| ------------------ | -------- | ------------------------------- | ---------------- | ------------------ |
| commit             | develop  | update GitVersion configuration | 0.4.0-alpha.2    | 0.4.0-alpha.2      |
| create new feature | arch-900 |                                 | 0.4.0-arch-900.1 | 0.4.0-arch-900.1+2 |
| commit             | arch-899 | update file 5                   | 0.4.0-arch-900.1 | 0.4.0-arch-900.1+3 |
| close feature      | arch-890 |                                 |                  |                    |
|                    | develop  |                                 | 0.4.0-alpha.4    | 0.4.0-alpha.4      |
| commit             | develop  | update readme                   | 0.4.0-alpha.5    | 0.4.0-alpha.5      |
| commit             | develop  | update readme again             | 0.4.0-alpha.6    | 0.4.0-alpha.6      |
