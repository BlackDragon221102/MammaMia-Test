name: Update Domains

on:
  schedule:
    - cron: "0 20 * * *"  # Esegui alle 20:00 ogni giorno
  workflow_dispatch:      # Permette di avviare manualmente il workflow

permissions:
  contents: write  # Necessario per pushare le modifiche

jobs:
  update-domains:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v3

      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.12'

      - name: Install dependencies
        run: |
          pip install requests urllib3

      - name: Update domains in config.json
        run: |
          python update_domains.py

      - name: Clean up backup files
        run: |
          rm -f config.json.bak_*

      - name: Commit and push changes
        run: |
          git config --global user.email "github-actions[bot]@users.noreply.github.com"
          git config --global user.name "github-actions[bot]"
          git add config.json
          if git diff --staged --quiet; then
            echo "✅ Nessuna modifica da committare"
          else
            git commit -m "🔄 Aggiornamento domini [$(date +'%Y-%m-%d %H:%M')]"
            git push
            echo "✅ Modifiche committate con successo"
          fi
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
