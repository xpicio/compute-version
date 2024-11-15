# compute-version

Local develop branch:

```
docker run --rm -e BUILD_NUMBER=899 -v $(pwd):/repo gittools/gitversion:6.0.4 \
    /repo \
    /nocache \
    /config /repo/Gitversion.yml \
    /b develop
```

Local main branch:

```
docker run --rm -e BUILD_NUMBER=899 -v $(pwd):/repo gittools/gitversion:6.0.4 \
    /repo \
    /nocache \
    /config /repo/Gitversion.yml \
    /b main
```

Local production:

```
docker run --rm -e BUILD_NUMBER=899 -v $(pwd):/repo gittools/gitversion:6.0.4 \
    /repo \
    /nocache \
    /config /repo/Gitversion.prod.yml \
    /b main
```

## Compute Behavior

Start from tag v0.2.4 with conventional commits messages.

| action                         | branch   | commit message                         | SemVer           | FullSemVer         |
| ------------------------------ | -------- | -------------------------------------- | ---------------- | ------------------ |
| commit                         | develop  | chore: update GitVersion configuration | 0.3.0-alpha.1    |                    |
| commit                         | develop  | fix: update file                       | 0.3.0-alpha.2    |                    |
| commit                         | develop  | fix: update file 2                     | 0.3.0-alpha.3    |                    |
| create new feature             | arch-899 |                                        | 0.3.0-arch-899.1 | 0.3.0-arch-899.1+3 |
| commit                         | arch-899 | fix: update file 3                     | 0.3.0-arch-899.1 | 0.3.0-arch-899.1+4 |
| commit                         | arch-899 | feat: update file 4                    | 0.3.0-arch-899.1 | 0.3.0-arch-899.1+5 |
| close feature                  | arch-899 |                                        |                  |                    |
|                                | develop  |                                        | 0.3.0-alpha.6    | 0.3.0-alpha.6      |
| create release                 |          |                                        |                  |                    |
| close release                  |          |                                        |                  |                    |
|                                | develop  |                                        | 0.3.0-alpha.8    | 0.3.0-alpha.8      |
|                                | main     |                                        | 0.3.0-rc.7       | 0.3.0-rc.7         |
| before tag (production deploy) | main     |                                        | 0.3.0-7          | 0.3.0-7            |

Start from tag v0.3.0.

| action                         | branch   | commit message                  | SemVer           | FullSemVer         |
| ------------------------------ | -------- | ------------------------------- | ---------------- | ------------------ |
| commit                         | develop  | update GitVersion configuration | 0.4.0-alpha.2    | 0.4.0-alpha.2      |
| create new feature             | arch-900 |                                 | 0.4.0-arch-900.1 | 0.4.0-arch-900.1+2 |
| commit                         | arch-899 | update file 5                   | 0.4.0-arch-900.1 | 0.4.0-arch-900.1+3 |
| close feature                  | arch-890 |                                 |                  |                    |
|                                | develop  |                                 | 0.4.0-alpha.4    | 0.4.0-alpha.4      |
| commit                         | develop  | update readme                   | 0.4.0-alpha.5    | 0.4.0-alpha.5      |
| commit                         | develop  | update readme again             | 0.4.0-alpha.6    | 0.4.0-alpha.6      |
| create release                 |          |                                 |                  |                    |
| commit                         | develop  | update readme in release        |                  |                    |
| close release                  |          |                                 |                  |                    |
|                                | develop  |                                 | 0.4.0-alpha.9    | 0.4.0-alpha.9      |
|                                | main     |                                 | 0.3.1-rc.8       | 0.3.1-rc.8         |
| before tag (production deploy) | main     |                                 | 0.3.1-8          | 0.3.1-8            |

Start from tag v0.3.1 with conventional commits messages.

| action                         | branch   | commit message                                 | SemVer           | FullSemVer         |
| ------------------------------ | -------- | ---------------------------------------------- | ---------------- | ------------------ |
| commit                         | develop  | ci: update GitVersion configuration and readme | 0.4.0-alpha.2    | 0.4.0-alpha.2      |
| create new feature             | arch-901 |                                                |                  |                    |
| commit                         | arch-901 | fix: update file 6                             | 0.4.0-arch-901.1 | 0.4.0-arch-901.1+3 |
| close feature                  | arch-901 |                                                |                  |                    |
|                                | develop  |                                                | 0.4.0-alpha.4    | 0.4.0-alpha.4      |
| commit                         | develop  | fix: update file 7                             | 0.4.0-alpha.5    | 0.4.0-alpha.5      |
| commit                         | develop  | chore: update file 8                           | 0.4.0-alpha.6    | 0.4.0-alpha.6      |
| create release                 |          |                                                |                  |                    |
| close release                  |          |                                                |                  |                    |
|                                | develop  |                                                | 0.4.0-alpha.8    | 0.4.0-alpha.8      |
|                                | main     |                                                | 0.3.2-rc.7       | 0.3.2-rc.7         |
| before tag (production deploy) | main     |                                                | 0.3.2-7          | 0.3.2-7            |

Start from tag v0.3.2 with conventional commits messages.

| action                         | branch     | commit message     | SemVer        | FullSemVer     |
| ------------------------------ | ---------- | ------------------ | ------------- | -------------- |
| create new hotfix              | epic-error |                    |               |                |
|                                | epic-error |                    | 0.3.3-beta.1  | 0.3.3-beta.1+4 |
| commit                         | epic-error | fix: error         | 0.3.3-beta.1  | 0.3.3-beta.1+5 |
| close hotfix                   |            |                    |               |                |
|                                | develop    |                    | 0.4.0-alpha.7 | 0.4.0-alpha.7  |
|                                | main       |                    | 0.3.3-rc.6    | 0.3.3-rc.6     |
| before tag (production deploy) | main       |                    | 0.3.3-6       | 0.3.3-6        |
|                                | develop    |                    | 0.4.0-alpha.1 | 0.4.0-alpha.1  |
| commit                         | develop    | doc: update readme | 0.4.0-alpha.2 | 0.4.0-alpha.2  |

Start from tag v0.4.1.

| action                         | branch       | commit message                               | SemVer           | FullSemVer          |
| ------------------------------ | ------------ | -------------------------------------------- | ---------------- | ------------------- |
| commit                         | develop      | update GitVersion configuration (with Minor) | 0.5.0-alpha.9    | 0.5.0-alpha.9       |
| create new feature             | arch-903     |                                              |                  |                     |
| commit                         | arch-903     | update file 99                               | 0.5.0-arch-903.1 | 0.5.0-arch-903.1+10 |
| close feature                  | arch-903     |                                              |                  |                     |
|                                | develop      |                                              | 0.5.0-alpha.11   | 0.5.0-alpha.11      |
| commit                         | develop      | update readme 99                             | 0.5.0-alpha.12   | 0.5.0-alpha.12      |
| commit                         | develop      | update again 99                              | 0.5.0-alpha.13   | 0.5.0-alpha.13      |
| create release                 |              |                                              |                  |                     |
| close release                  |              |                                              |                  |                     |
|                                | develop      |                                              | 0.5.0-alpha.15   | 0.5.0-alpha.15      |
|                                | main         |                                              | 0.5.0-rc.14      | 0.5.0-rc.14         |
| before tag (production deploy) | main         |                                              | 0.5.0-14         | 0.5.0-14            |
|                                | develop      |                                              | 0.6.0-alpha.1    | 0.6.0-alpha.1       |
|                                | develop      | update readme 199                            | 0.6.0-alpha.2    | 0.6.0-alpha.2       |
| create new hotfix              | epic-error-3 |                                              |                  |                     |
|                                | epic-error-3 |                                              | 0.6.0-beta.1     | 0.6.0-beta.1+0      |
| commit                         | epic-error-3 | update readme in hotfix 99                   | 0.6.0-beta.1     | 0.6.0-beta.1+1      |
| commit                         | epic-error-3 | update readme in hotfix 99-2                 | 0.6.0-beta.1     | 0.6.0-beta.1+2      |
| commit                         | epic-error-3 | update readme in hotfix 99-3                 | 0.6.0-beta.1     | 0.6.0-beta.1+3      |
| close hotfix                   |              |                                              |                  |                     |
|                                | develop      |                                              | 0.6.0-alpha.7    | 0.6.0-alpha.7       |
| commit                         | develop      | update readme                                | 0.6.0-alpha.8    | 0.6.0-alpha.8       |
|                                | main         |                                              | 0.6.0-rc.4       | 0.6.0-rc.4          |
| before tag (production deploy) | main         |                                              | 0.6.0-4          | 0.6.0-4             |
|                                | develop      |                                              | 0.7.0-alpha.4    | 0.7.0-alpha.4       |
| commit                         | develop      | last update                                  | 0.7.0-alpha.5    | 0.7.0-alpha.5       |
