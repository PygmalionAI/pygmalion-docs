## Pygmalion Docs

Running the docs on your PC locally:

#### Requirements:
- `git`
- `nodejs`

##### Install the requirements (Windows):
- Open PowerShell (Win10) or Terminal (Win11)
- `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`
- `irm get.scoop.sh | iex`
- `scoop install git`
- `scoop bucket add extras`
- `scoop install nodejs`

##### Install the requirements (Linux)
- All package managers have both `git` and `nodejs`.

#### Installation 

- Clone the repo:
```bash
git clone https://github.com/AlpinDale/pygmalion-docs && cd pygmalion-docs
```
- Run the docs using `retypeapp`
```bash
npx retypeapp watch
```

***

Please regularly update with `git pull`. This is still a WIP so updates are expected at an hourly basis.
