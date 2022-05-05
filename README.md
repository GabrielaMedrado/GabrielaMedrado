### Olá, meu povo! Tudo bem? 

<p> Meu nome é Gabriela, seja muito bem-vindo! Por aqui a gente continua estudando e codando para deixar este espaço bonitão e cheio de projetos legais. Sou formada em jornalismo e me encontro em transição de carreira. Estudante de Front-end pela Laboratória, em breve teremos uma desenvolvedora real, oficial por aqui. Até mais! </p>

##

<div align="center">
<a href="https://github.com/GabrielaMedrado">
  <img height="180em" src="https://github-readme-stats.vercel.app/api/top-langs/?username=GabrielaMedrado&layout=compact&langs_count=7&theme=bear">
  <img height="180em" src="https://github-readme-stats.vercel.app/api?username=GabrielaMedrado&show_icons=true&theme=bear&include_all_commits=true&count_private=true">
  
</div>
  
  ##
  
  <div align="center"> 
  <a href = "mailto:gabrieladmr@gmail.com"><img src="https://img.shields.io/badge/-Gmail-%23333?style=for-the-badge&logo=gmail&logoColor=white" target="_blank"> </a>
  <a href="https://www.linkedin.com/in/gabrielamedrado/" target="_blank"><img src="https://img.shields.io/badge/-LinkedIn-%230077B5?style=for-the-badge&logo=linkedin&logoColor=white" target="_blank"></a> 
   
</div>
  
  ##
  
# Nome da Actions:  
name: Snake Game

# Controlador do tempo que sera feito a atualização dos arquivos.
on:
  schedule:
      # Será atualizado a cada 5 horas.
    - cron: "0 */5 * * *"

# Permite executar na na lista de Actions (utilizado para testes de build).
  workflow_dispatch:

# Regras
jobs:
  build:
    runs-on: ubuntu-latest
    steps:

    # Checks repo under $GITHUB_WORKSHOP, so your job can access it
      - uses: actions/checkout@v2

    # Repositorio que será utilizado para gerar os arquivos.
      - uses: Platane/snk@master
        id: snake-gif
        with:
          github_user_name: GabrielaMedrado
          gif_out_path: dist/github-contribution-grid-snake.gif
          svg_out_path: dist/github-contribution-grid-snake.svg

      - run: git status

      # Para as atualizações.
      - name: Push changes
        uses: ad-m/github-push-action@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          branch: master
          force: true

      - uses: crazy-max/ghaction-github-pages@v2.1.3
        with:
          # the output branch we mentioned above
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
