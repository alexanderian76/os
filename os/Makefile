BUILD_DIR=../build/os
OS=$(BUILD_DIR)/os

CFLAGS+=-ffreestanding -nostdlib -m32 -gdwarf-4 -ggdb3 -fno-stack-protector

OS_SRCS := $(wildcard *.c)
OS_OBJS := $(patsubst %.c, $(BUILD_DIR)/%.o, $(OS_SRCS))

all: $(OS)

$(BUILD_DIR)/%.o: %.c
	gcc $(CFLAGS) -m32 -c $< -o $@
	
$(OS): $(OS_OBJS)
	nasm -f elf32 kernel.asm -o $(BUILD_DIR)/kasm.o
	ld -m elf_i386 -nmagic -Tos.lds $(OS_OBJS) $(BUILD_DIR)/kasm.o -o $@
	
	
clean:
	rm $(OS_OBJS)
