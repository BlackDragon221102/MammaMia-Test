name: Update and Deploy
 
on:
  schedule:
    - cron: "30 5 * * *"  # Esegui ogni giorno alle 05:30
  workflow_dispatch:        # Permette di avviare manualmente il workflow
 
jobs:
  update_and_deploy:
    runs-on: ubuntu-latest
 
    steps:
      # Checkout del repository
      - name: Checkout repository
        uses: actions/checkout@v3
 
      # Configura Git
      - name: Set up Git
        run: |
          git config --global user.name "tuo_nome"
          git config --global user.email "tuo_email@example.com"
 
      # Esegui lo script di aggiornamento
      - name: Run update script
        run: bash ./update_and_deploy.sh
