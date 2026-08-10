# WLED 0.15.4 ESP32-ETH01 - 40 DDP

Workflow pronto per compilare WLED v0.15.4 per ESP32-ETH01 / WT32-ETH01 con Ethernet e 40 slot bus totali, utilizzabili tutti come uscite virtuali DDP se non vengono configurate uscite fisiche.

## Uso
1. Crea un repository GitHub vuoto e carica il contenuto di questa cartella mantenendo `.github/workflows/build.yml`.
2. Apri **Actions** > **Build WLED 0.15.4 ESP32-ETH01 40 DDP**.
3. Premi **Run workflow**.
4. A build conclusa scarica l'artifact **WLED_0.15.4_ESP32-ETH01_40DDP**.
5. Dentro trovi `WLED_0.15.4_ESP32-ETH01_40DDP.bin` e il relativo SHA-256.

## Modifiche applicate
- `WLED_MIN_VIRTUAL_BUSSES`: `6` -> `21`.
- Ethernet predefinita: `WT32-ETH01`.
- Build environment ufficiale: `esp32_eth` di WLED v0.15.4.

Nota: 19 bus fisici + 21 bus virtuali = 40 slot totali. Se configuri un bus fisico, rimangono 39 slot per uscite virtuali DDP.
