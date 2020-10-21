# waka-box

Using <https://github.com/YouEclipse/waka-box-go>, you don't need to fork the repo.

```yml
# .github/workflows/schedule.yml

name: waka-box

on:
  push:
    branches:
      - master
  schedule:
    - cron: "0 0 * * *"

jobs:
  update:
    runs-on: ubuntu-latest
    env:
      WAKATIME_API_KEY: ${{ secrets.WAKATIME_API_KEY }}
      GH_TOKEN: ${{ secrets.GH_TOKEN }}
      GIST_ID: 279142384e4034402d18ea6b994a6e46
      GIST_BARSTYLE: SOLIDLT
      GIST_BARLENGTH: -1

    steps:
      - name: Set up Go 1.x
        uses: actions/setup-go@v2
        with:
          go-version: ^1.14
        id: go

      - name: Update gist
        run: |
          git clone https://github.com/YouEclipse/waka-box-go.git
          cd waka-box-go
          go run ./cmd/box/main.go
```
