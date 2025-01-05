---
title: "elf文件头信息"
categories:
  - coding
tags:
---

- 0x00 - 0x03: 魔数字节
- 0x04: 类(`02` 表示这是一个 64 位 ELF 文件（`01` 是 32 位）)
- 0x05:数据编码(`01` 表示采用小端存储（Little Endian）)
- 0x06:版本(`01` 表示当前版本)
- 0x07:操作系统ABI(`00` 表示 UNIX 系统 V)
- 0x08:ABI版本(`00` 表示 ABI 的版本号为 0)
- 0x09-0x0F:padding
- 0x10-0x11:Type(`01` 表示这是一个可重定位文件（Relocatable file）)
- 0x12-0x13:Machine(`3e` 表示这是一个 x86-64 架构（Advanced Micro Devices X86-64）)
- 0x14-0x17:版本(`01` 表示当前版本)
- 0x18-0x1F:入口点地址(入口点地址是 `0x0`，即没有指定入口点)
- 0x20-0x27:程序头的开始(表示程序头从文件开始处偏移 `0x0` 字节。由于这是一个可重定位文件（REL），所以没有程序头)
- 0x28-0x2F:节头的开始(节头从文件偏移 `0x9f00` 字节处开始)
- 0x30-0x33:Flags(00表示没有特殊标志)
- 0x34-0x35:ELF文件头大小
-  0x36-0x37:ELF程序头大小
-  0x38-0x39:ELF程序头数目
-  0x3A-0x3B:ELF节头大小
- 0x3C-0x3D:节头数目
- 0x3E-0x3F节头字符串表索引

### section header struct

```
typedef struct { 
	uint32_t sh_name; // 段的名称索引（相对于字符串表） 
	uint32_t sh_type; // 段的类型（如 SHT_PROGBITS, SHT_NOBITS） 
	uint64_t sh_flags; // 段的标志（如 SHF_ALLOC, SHF_EXECINSTR） 
	uint64_t sh_addr; // 段的虚拟地址（加载时的地址） 
	uint64_t sh_offset; // 段在文件中的偏移 
	uint64_t sh_size; // 段的大小 
	uint32_t sh_link; // 与段相关的链接表索引（例如，对于符号表，该值是字符串表的索引） 
	uint32_t sh_info; // 与段相关的附加信息 
	uint64_t sh_addralign; // 段的地址对齐方式 
	uint64_t sh_entsize; // 如果段包含表格，这个字段是表项的大小 
} Elf64_Shdr;
```
