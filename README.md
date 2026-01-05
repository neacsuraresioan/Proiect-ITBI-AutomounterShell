# Proiect-ITBI-AutomounterShell
Proiect ITBI, AutomounterShell
list_devices(){
	echo "=== dispozitive disponibile ==="
	lsblk -pnro NAME,TYPE,TRAN,FSTYPE,LABEL,UUID,MOUNTPOINT
}
