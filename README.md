
<h2 align="left">Hi 👋! My name is Jonathan and I'm a SOC Analyst from NYC.</h2>

###

<div align="center">
  <img src="https://github-readme-stats.vercel.app/api?username=Dvlprjayman&hide_title=false&hide_rank=false&show_icons=true&include_all_commits=true&count_private=true&disable_animations=false&theme=dracula&locale=en&hide_border=false" height="150" alt="stats graph"  />
  <img src="https://github-readme-stats.vercel.app/api/top-langs?username=Dvlprjayman&locale=en&hide_title=false&layout=compact&card_width=320&langs_count=5&theme=dracula&hide_border=false" height="150" alt="languages graph"  />
</div>

###

<div align="left">
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/python/python-original.svg" height="30" alt="python logo"  />
  <img width="12" />
  <img src="https://cdn.simpleicons.org/gnubash/4EAA25" height="30" alt="bash logo"  />
  <img width="12" />
  <img src="https://cdn.simpleicons.org/mysql/4479A1" height="30" alt="mysql logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=linux" height="30" alt="linux logo"  />
  <img width="12" />
  <img src="https://cdn.simpleicons.org/git/F05032" height="30" alt="git logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/putty/putty-original.svg" height="30" alt="putty logo"  />
  <img width="12" />
  <img src="https://cdn.simpleicons.org/docker/2496ED" height="30" alt="docker logo"  />
  <img width="12" />
  <img src="https://skillicons.dev/icons?i=github" height="30" alt="github logo"  />
  <img width="12" />
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/windows8/windows8-original.svg" height="30" alt="windows8 logo"  />
</div>

###

<div align="left">
  <a href="https://www.linkedin.com/in/jonathan-vargas-cybersa/" target="_blank">
    <img src="https://img.shields.io/static/v1?message=LinkedIn&logo=linkedin&label=&color=0077B5&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="linkedin logo"  />
  </a>
  <a href="https://tryhackme.com/p/DvlprJay" target="_blank">
    <img src="https://img.shields.io/static/v1?message=TryHackMe&logo=tryhackme&label=&color=88cc14&logoColor=white&labelColor=&style=for-the-badge" height="35" alt="tryhackme logo"  />
  </a>
</div>

###

<br clear="both">

<img src="https://raw.githubusercontent.com/Dvlprjayman/Dvlprjayman/output/snake.svg" alt="Snake animation" />

###



name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - master

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}


