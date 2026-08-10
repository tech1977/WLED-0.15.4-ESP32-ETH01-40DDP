# WLED 0.15.4 - ESP32-ETH01 - 40 DDP - Tech1977

Build personalizzata basata su **WLED v0.15.4 ufficiale**.

Nome visualizzato nel pannello Info:

`v.0.15.4 test ddp "Tech1977"`

## Hardware target

- ESP32 classico
- WT32-ETH01 / ESP32-ETH01
- Ethernet abilitata
- Environment PlatformIO: `esp32_eth`
- Ethernet predefinita: WT32-ETH01

## Funzioni della build

| Funzione | Valore |
|---|---:|
| WLED base | 0.15.4 |
| Uscite virtuali DDP | fino a 40 |
| Segmenti | 40, ID 0-39 |
| MAX_NUM_SEGMENTS | 40 |
| MAX_SEGMENT_DATA | 51.200 byte |
| Ethernet | WT32-ETH01 |
| Firmware OTA | sì |
| Nome custom | Tech1977 |

## Modifiche rispetto a WLED 0.15.4 originale

### 40 uscite DDP

Aumentata la capacità delle uscite virtuali.

Per ESP32 classico:

`WLED_MIN_VIRTUAL_BUSSES: 6 -> 21`

La gestione della configurazione è stata modificata per permettere
la persistenza delle uscite virtuali DDP anche dopo reboot.

### Persistenza DDP

Modificato il caricamento di `cfg.json` affinché i bus virtuali DDP
non vengano conteggiati come bus fisici nel limite `WLED_MAX_BUSSES`.

Questo risolve il problema per cui, dopo Save + reboot,
le uscite LED potevano risultare vuote.

### Output 36-39

WLED 0.15.4 utilizza identificatori a singolo carattere nella pagina
LED Preferences.

Mapping utilizzato:

0-9  -> output 0-9
A-Z  -> output 10-35
a-d  -> output 36-39

Sono stati adattati:

`settings_leds.htm`
`set.cpp`
`xml.cpp`

### 40 segmenti

Modificato:

`MAX_NUM_SEGMENTS: 32 -> 40`

I segmenti disponibili sono quindi:

`Segment 0 ... Segment 39`

### RAM effetti

Mantenuta la formula originale WLED:

`MAX_SEGMENT_DATA = MAX_NUM_SEGMENTS * 1280`

Con 40 segmenti:

`40 * 1280 = 51.200 byte max`

La memoria non viene necessariamente occupata tutta:
è il limite massimo disponibile per i dati runtime degli effetti.

### Auto segments

Aggiunto controllo per evitare che `makeAutoSegments()`
superi `MAX_NUM_SEGMENTS`.

### Nome versione personalizzato

Nel pannello Info viene visualizzato:

`v.0.15.4 test ddp "Tech1977"`

Il VERSION ID originale WLED rimane invariato.

## Test da verificare

| Test | Stato |
|---|---|
| Ethernet WT32-ETH01 | OK |
| 40 output visibili | OK |
| Segmenti 0-39 | OK |
| Save 40 DDP | da verificare |
| 40 DDP dopo reboot | da verificare |
| Effetti segmenti 32-39 | da verificare |
| Preset con 40 segmenti | da verificare |
| Restore preset dopo reboot | da verificare |
| Stress RAM / 40 effetti | da verificare |

## Firmware

Nome build:

`WLED_v0.15.4_test_DDP_Tech1977.bin`

## Changelog

### r1 - 10-08-2026

Prima build Tech1977:

- WLED 0.15.4
- ESP32-ETH01 Ethernet
- 40 output DDP
- persistenza DDP modificata
- 40 segmenti
- 51.200 byte MAX_SEGMENT_DATA
- mapping output 36-39 tramite a-d
- label `v.0.15.4 test ddp "Tech1977"`

## Note

Questa è una build sperimentale personalizzata e non una release
ufficiale del progetto WLED.

Repository originale: wled/WLED
