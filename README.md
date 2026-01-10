list_devices(){
	echo "=== dispozitive disponibile ==="
	lsblk -pnro NAME,TYPE,TRAN,FSTYPE,LABEL,UUID,MOUNTPOINT
}
mount_devices (){
	dev="$1"

	if [ -z "$dev" ]; then
		echo "ERROR: no device provided"
		echo "Example: /dev/sdb1"
		return 1
	fi

	if findmnt -n "$dev" >/dev/null 2>&1; then
		echo "Device already mounted: $dev"
		return 0
	fi
	
	name=$(basename "$dev")
	mp="media/automount/$name"

	sudo mkdir -p "$mp"
	sudo mount "$dev" "$mp"

	echo "Mounted $dev at $mp"
}
