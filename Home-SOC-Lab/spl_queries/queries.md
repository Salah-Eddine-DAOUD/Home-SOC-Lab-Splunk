# Requêtes SPL Utilisées dans le SOC Lab

## 1. Détection d'attaque Brute Force (Extraction IP et Comptage)

spl
index=soc_lab "Failed password" NOT "127.0.0.1"
| rex field=\_raw "from (?<src_ip>\d+\.\d+\.\d+\.\d+)"
| stats count by src_ip
| sort -count

## 2.Détection des connexions réussies

spl
index=soc_lab "Accepted password" | stats count

## 3.Détection de Scan de Ports (Nmap)

spl
index=soc_lab sourcetype=syslog "UFW BLOCK"
| rex field=\_raw "SRC=(?<src_ip>\d+\.\d+\.\d+\.\d+)"
| rex field=\_raw "DPT=(?<dest_port>\d+)"
| stats dc(dest_port) as scanned_ports by src_ip
| where scanned_ports > 10
