

SRC = \
      common.c\
      efi.c\
      main.c\
      shell.c

OBJ = $(SRC:.c=.o)

NAME =main.efi


all: $(NAME)

%.o: %.c
	clang -target x86_64-pc-win32-coff -o $@ -c $<

$(NAME): $(OBJ)
	lld-link /subsystem:efi_application /entry:efi_main /out:$(NAME) $(OBJ)

run: fs/EFI/BOOT/BOOTX64.EFI
	qemu-system-x86_64 -bios /usr/share/ovmf/OVMF.fd -hda fat:fs

clean:
	rm -rf *~ fs

.PHONY: clean
