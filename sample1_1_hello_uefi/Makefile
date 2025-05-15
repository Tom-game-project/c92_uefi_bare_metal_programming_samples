
NAME = main.efi


all:$(NAME)

%.o: %.c
	clang -target x86_64-pc-win32-coff -o $@ -c $<

%.efi: %.o
	lld-link /subsystem:efi_application /entry:efi_main /out:$@ $<


fs/EFI/BOOT/BOOTX64.EFI: $(NAME)
	mkdir -p fs/EFI/BOOT/
	touch fs/EFI/BOOT/BOOTX64.EFI
	cp $(NAME) fs/EFI/BOOT/BOOTX64.EFI


# RELEASEX64_OVMF.fdはUEFIのファームウェアのバイナリ
# CPUの電源が入ったときに一番最初に実行される
run: fs/EFI/BOOT/BOOTX64.EFI
	qemu-system-x86_64 -bios ../third_party/ovmf/RELEASEX64_OVMF.fd -drive format=raw,file=fat:rw:fs

clean:
	rm -rf *~ fs

.PHONY: clean
