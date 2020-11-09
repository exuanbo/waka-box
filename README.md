# waka-box

Using <https://github.com/antfu/waka-box>, you don't need to fork the repo.

```yml
# .github/workflows/schedule.yml

name: waka-box

on:
  push:
    branches:
      - master
  schedule:
    - cron: "0 */12 * * *"

jobs:
  update:
    runs-on: ubuntu-latest

    steps:
      - name: Use antfu/waka-box
        run: |
          git clone https://github.com/antfu/waka-box.git
          cd waka-box
          npm ci
          node ./index.js
        env:
          GH_TOKEN: ${{ secrets.GH_TOKEN }}
          GIST_ID: 279142384e4034402d18ea6b994a6e46
          WAKATIME_API_KEY: ${{ secrets.WAKATIME_API_KEY }}
```
