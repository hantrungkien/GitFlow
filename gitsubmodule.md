- Add submodule

```
git submodule add @repo @path
```

- Add all submodules in .gitmodules

```
git submodule sync --recursive

git submodule update --init --recursive

git pull origin develop && git submodule foreach --recursive git pull origin develop

git submodule foreach git checkout develop

git submodule foreach git pull
```

- Checkout & Pull a branch on all submodules

```
git submodule foreach "(git checkout branch_name; git pull)&"
```

- Delete a submodule

```
1. rm -rf [path_sub_module]

2. git rm -r [path_sub_module]

3. git add .gitmodules

4. Delete the relevant section from .git/config.

5. git rm --cached [path_sub_module]

6. rm -rf .git/modules/[path_sub_module]
```
