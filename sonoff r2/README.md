# Comandos para instalar EspHome en un Sonoff en modo DIY


```bash
nmap -p 8081 --open 192.168.1.0/24

curl -XPOST --header "Content-Type: application/json" --data-raw "{\"data\": {}}" "http://${SONOFF_IP}:8081/zeroconf/info"

curl -XPOST --header "Content-Type: application/json" --data-raw "{\"data\": {}}" "http://${SONOFF_IP}:8081/zeroconf/ota_unlock"

SONOFF_HASH=`sha256sum sonoff-mini.bin | cut -d ' ' -f 1`


curl -XPOST --header "Content-Type: application/json" --data-raw "{\"data\": {\"downloadUrl\":\"${SONOFF_URL}\", \"sha256sum\":\"${SONOFF_HASH}\"}}" "http://${SONOFF_IP}:8081/zeroconf/ota_flash"

```